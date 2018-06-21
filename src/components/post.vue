<template>
  <div class="post">
    <img class="post_image" v-bind:src="getAssetPath(image)" />
    <img class='post_branding' src="../assets/logo_and_hamburger.svg" alt="">

    <div class="post_title-container is-editing" v-if="isEditing">
      <button class="post_icon post_icon--cancel" @click="discardChanges"></button>
      <button class="post_icon post_icon--save" @click="saveChanges" :disabled="invalidTitle"></button>
      <div class="post_title">
        <input type="text" class="title_input" v-model="title">
        <div class="title_slug" :class="{ 'is-invalid': invalidTitle}">{{slug}}</div>
      </div>
    </div>
    <div class="post_title-container" v-else>
      <button class="post_icon post_icon--edit" @click="toggleEditMode"></button>
      <span class="post_title">{{title}}</span>
    </div>

    <div class="post_details">
      <div class="post_detail post_detail--author">{{author}}</div>
      <div class="post_detail post_detail--date">{{date}}</div>
      <ul class="post_detail post_detail--tags">
        <li v-for="tag in tags" class="post_tag">{{tag}}</li>
      </ul>
    </div>

    <div class="post_body" v-html="content"></div>
  </div>
</template>

<script>
export default {
  name: 'post',
  props: {
    title: String,
    author: String,
    date: String,
    tags: Array,
    image: String,
    content: String
  },
  data: function() {
    return {
      isEditing: false,
      originalTitle: null
    }
  },
  computed: {
    invalidTitle: function() {
      return this.title.length === 0;
    },
    slug: function() {
      if(this.title.length) {
        let slug = this.title.toLowerCase().replace(/\?|\.|\"|\'|\,|\;/g, '');
        return slug.split(' ').join('-');
      } else {
        return 'please enter a post title'
      }
    }
  },
  methods: {
    getAssetPath: function(asset) {
      return require('../assets/' + asset)
    },
    toggleEditMode: function() {
      this.originalTitle = this.title;
      this.isEditing = !this.isEditing;
    },
    discardChanges: function() {
      this.title = this.originalTitle;
      this.isEditing = false;
    },
    saveChanges: function() {
      this.isEditing = false;
    }
  }
}
</script>

<style lang="scss">
.post {
  display: grid;
  grid-template-columns: 70px repeat(8, 1fr) 70px;
  grid-template-rows: auto 130px auto;
}

.post_image {
  max-width: 100%;
  grid-column-start: 1;
  grid-column-end: span 10;
  grid-row-start: 1;
  z-index: 0;
}

.post_branding {
  grid-column-start: 8;
  grid-column-end: span 2;
  grid-row-start: 1;
  justify-self: end;
  z-index: 1;

  width: 200px;
  margin-top: 75px;
}

.post_title-container {
  grid-column-start: 3;
  grid-column-end: span 5;
  grid-row-start: 1;
  align-self: end;
  position: relative;
  top: 28px;
  z-index: 1;

  mix-blend-mode: screen;
}

.post_icon {
  position: absolute;
  z-index: 1;

  width: 32px;
  height: 32px;
  border: 0;

  background-repeat: no-repeat;
  background-position: 50%;
  cursor: pointer;

  &:focus {
    outline: none;
  }
}

.post_icon--edit {
  top: -44px;
  left: -52px;

  background-color: #f3e13b;
  background-image: url(../assets/pencil.svg);
}


.post_title {
  position: relative;
  margin: 0;
  padding-top: 12px;

  background-color: #fff;
  color: #000;
  font-family: Copernicus;
  font-size: 54px;

  &:after {
    position: absolute;
    top: 0px;
    right: 100%;
    bottom: 0;
    left: -20px;

    background: #fff;
    content: '';
  }
}

.is-editing {
  top: 0;

  .post_title {
    padding: 20px 20px 0 0;
  }
}

.post_icon--cancel {
  top: -66px;
  left: -52px;

  background-color: #DC5730;
  background-image: url(../assets/x.svg);
}

.post_icon--save {
  top: -33px;
  left: -52px;

  background-color: #93CA48;
  background-image: url(../assets/checkmark.svg);

  &[disabled] {
    background-color: #3C3C3C;
    cursor: not-allowed;
  }
}

.title_input {
  box-sizing: border-box;
  width: 100%;
  margin-bottom: 9px;
  padding: 24px 22px;

  font-family: Copernicus;
  font-size: 44px;
}

.title_slug {
  color: #535353;
  font-family: Futura;
  font-size: 14px;

  &.is-invalid {
    color: #a3a3a3;
    font-style: italic;
  }

  &:before {
    margin-right: 5px;

    color: #a3a3a3;
    content: 'slug:';
    font-style: normal;
  }
}

.post_details {
  grid-column-start: 3;
  grid-row-start: 3;
}

.post_detail {
  border-top: 1px solid #dfdfdf;
  padding-top: 10px;
  padding-bottom: 36px;

  color: #a3a3a3;
  font-family: Futura;
  font-size: 10px;
  text-align: left;
  text-transform: uppercase;
}

.post_detail--author {
  color: #6f4f31;
  font-family: Copernicus;
  font-size: 12px;
  text-transform: capitalize;

  &:before {
    margin-right: 5px;

    color: #a3a3a3;
    content: 'By';
    font-family: Futura;
    font-size: 10px;
    text-transform: uppercase;
  }
}

.post_detail--date {
  padding-bottom: 28px;
}

.post_detail--tags {
  margin: 0;
  padding-left: 0;
}

.post_tag {
  display: block;
  margin-bottom: 4px;

  &:before {
    color: #bfbfbf;
    content: '#';
  }
}

.post_body {
  grid-column-start: 5;
  grid-column-end: span 4;
  grid-row-start: 3;

  color: #262626;
  font-family: Palatino;
  font-size: 14px;
  line-height: 24px;

  p:first-child {
    margin-top: 0;
  }
}

.post_location {
  color: #808080;
  font-family: Futura;
  font-size: 10px;
  text-transform: uppercase;
}

.post_pull-quote {
  position: relative;
  left: -46px;
  grid-column-start: 5;
  grid-column-end: span 4;

  color: #8a98a6;
  font-family: Copernicus;
  font-size: 30px;
  line-height: 38px;
}
</style>
