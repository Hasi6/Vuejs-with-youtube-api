<template>
  <div class="container">
    <SearchBar @termChange="onTermChanged"></SearchBar>
    <div class="row">
      <VideoDetails v-if="videos.length >0" :video="selectedVideo" />
      <VideoList :videos="videos" @videoSelect="onVideoSelect" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar/SearchBar";
import VideoList from "./components/VideoList/VideoList";
import VideoDetails from "./components/VideoDetails/VideoDetails";

const API_KEY = "AIzaSyBSmqszKFvQ9PssJL_TzNLyjFlaW_8iX8s";

export default {
  name: "app",
  components: {
    SearchBar,
    VideoList,
    VideoDetails
  },
  data() {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  methods: {
    async onTermChanged(word) {
      if (word === "") {
        this.videos = [];
      } else {
        try {
          const res = await axios.get(
            `https://www.googleapis.com/youtube/v3/search/`,
            {
              params: {
                key: API_KEY,
                type: "video",
                part: "snippet",
                q: word
              }
            }
          );
          this.videos = res.data.items;
          console.log(this.videos);
        } catch (err) {
          console.error(err.message);
        }
      }
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
};
</script>
<style>
</style>
