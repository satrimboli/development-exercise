<template>
  <div id="app">
    <post 
     image="Ji9qebSpSlSbnsWRZnDX__MG_9520.jpg"
     title="Are we out of the woods yet?" 
     author="Bob Loblaw"
     date="August 6, 2015"
     :tags="['environment', 'swift', 'fungus']"
     content= "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce non consequat ligula. Aenean efficitur tellus eu egestas mollis. Aenean ultrices sodales purus, a sodales ex imperdiet ut. Curabitur molestie eget diam id feugiat. Sed dignissim metus ut mauris varius lacinia. Fusce non felis quis libero finibus convallis. Suspendisse tincidunt nibh et placerat bibendum. Etiam ornare sit amet felis id commodo. Nunc id luctus metus. Aenean in felis et sapien volutpat dapibus quis quis massa. Donec sodales, arcu facilisis imperdiet fringilla, lectus lacus viverra orci, at malesuada mi lorem a ligula. Nullam eu lorem finibus, tincidunt nisi vitae, ornare lorem. Maecenas id semper dui. Vivamus in felis mi.

Etiam a tellus eu lorem scelerisque laoreet. Donec nec vehicula diam. Sed risus arcu, egestas eu urna sed, rhoncus accumsan odio. Vivamus vitae congue odio. Donec a commodo eros, eu eleifend odio. Donec interdum interdum sapien, eget viverra turpis venenatis id. Nullam ultricies, ligula a dictum blandit, lorem metus pellentesque nibh, id fringilla purus sapien eu ligula. Aenean bibendum lobortis vestibulum. Phasellus hendrerit sollicitudin ante, placerat imperdiet mi. Nam ultricies dolor elementum aliquet lobortis. Phasellus tincidunt imperdiet ipsum, in venenatis lorem tempus eget. Nam in dapibus diam, id convallis tortor. Nunc in ultrices tellus, eget consequat nisl.

Vestibulum porttitor nulla id velit tristique, sit amet fringilla elit euismod. Duis urna magna, condimentum quis orci eu, tristique posuere justo. Nullam fermentum neque ligula, sit amet convallis mi feugiat eu. Morbi sollicitudin sem nec tellus venenatis, a faucibus lectus finibus. Ut eu aliquet nibh. Cras tristique nulla at enim condimentum convallis. Nam eu interdum nunc, quis venenatis urna. Nulla mattis ut nibh id ornare. Etiam sed orci a sem efficitur malesuada. Sed mattis elementum urna a fringilla. Suspendisse potenti.

Phasellus gravida sit amet tellus sit amet sagittis. Nam ac tempor lectus, at iaculis nulla. Nam eu posuere eros. In iaculis diam a turpis pretium faucibus. Etiam volutpat feugiat nisl non lacinia. Ut aliquam elementum sem, aliquet convallis arcu accumsan ultrices. Donec porttitor tortor sit amet vulputate finibus. Morbi erat risus, laoreet vel ex tristique, pretium fermentum mauris. Cras vel ante nulla.

Sed lectus ligula, tincidunt vitae ullamcorper quis, pulvinar quis tortor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Aenean ultrices posuere risus eu dignissim. Praesent efficitur, tortor sit amet rhoncus dapibus, erat elit dignissim erat, a varius mauris turpis at neque. Suspendisse quis aliquet neque, non aliquet leo. Suspendisse purus quam, cursus quis ligula ut, placerat tincidunt elit. Fusce a mauris id justo pellentesque pellentesque et at tortor. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam tristique a purus et tincidunt. Suspendisse dictum neque id sagittis consectetur. Maecenas ultricies viverra eros id euismod. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus."
    
    />
  </div>
</template>

<script>
import post from './components/post.vue'

export default {
  name: 'app',
  components: {
    post
  }
}
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
