<template>
  <li class="list-group-item" @click="onVideoSelect">
    <img :src="video.snippet.thumbnails.default.url" class="me-3" />
      {{video.snippet.title}}
  </li>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['video'],
    methods: {
      onVideoSelect() {
        this.$emit('videoSelect', this.video)
      }
    }
}
</script>

<style scoped> 
li {
  cursor: pointer;
}
li:hover {
   background-color: azure;
}
</style>

