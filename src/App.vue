<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"/>
    <div class="row">
      <div class="col-md-8">
        <VideoDetail :video="selectedVideo"/>
      </div>
      <div class="col-md-4">
        <VideoList @videoSelect="onVideoSelect" :videos="videos"/>
      </div>
    </div>
  </div>
</template>


<script>

import axios from 'axios'
import SearchBar from './components/SearchBar.vue'
import VideoList from './components/VideoList.vue'
import VideoDetail from './components/VideoDetail.vue'

const API_KEY = "AIzaSyAhXQoyMw6lnXq8d8QIu2k4mx_VuMibrQM"

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
        videos: [],
        selectedVideo: null
    }
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video
    },
    onTermChange(searchTerm) {
      axios.get("https://www.googleapis.com/youtube/v3/search", {
        params: {
          part: "snippet",
          key: API_KEY,
          q: searchTerm,
          // maxResults: 3
        },
      }).then(response => {
        this.videos = response.data.items;
      });
    }
  }
}
</script>