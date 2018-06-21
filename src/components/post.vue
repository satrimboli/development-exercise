<template>
  <div class="post">
    <img class="post_image" v-bind:src="getAssetPath(image)" />
    <div class="post_icon--edit"></div>
    <h1 class="post_title">{{title}}</h1>
    <div class="post_details">
      <div class="post_author"></div>
      <div class="post_date">{{date}}</div>
      <ul class="post_tags">
        <li v-for="tag in tags" class="post_tag">{{tag}}</li>
      </ul>
    </div>
    <div class="post_body">
      {{content}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'post',
  props: {
    title: String,
    author: String,
    date: String,
    tags: Object,
    content: String,
    pullQuote: String,
    image: String
  },
  data: function() {
    return {
      isEditing: false
    }
  },
  methods: {
    getAssetPath: function(asset) {
      return require('../assets/' + asset)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.post_icon--edit {
  width: 42px;
  height: 42px;
  background-image: url(../assets/pencil.svg);
  background-repeat: no-repeat;
  background-color: #f3e13b;
  background-position: 50%;
}
.post_image {
  max-width: 100%;
}

.post_title {
  background-color: #fff;
  mix-blend-mode: screen;
  font-size: 50px;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
