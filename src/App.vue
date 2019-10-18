<template>
  <div>
    <SearchBar @termChange="onTermChanged"></SearchBar>
    <VideoList :list="list" />
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar/SearchBar";
import VideoList from "./components/VideoList/VideoList";

const API_KEY = "AIzaSyBDTIkrq_EQJUC8o2tW1-ASi7LIN0nbaUA";

export default {
  name: "app",
  components: {
    SearchBar,
    VideoList
  },
   data(){
    return {
      list: []
    };
  },
  methods: {
      onTermChanged(word) {
          axios.get(
          `https://www.googleapis.com/youtube/v3/search/`,
          {
            params: {
              key: API_KEY,
              type: "video",
              part: "snippet",
              q: word
            }
          }
        ).then(res=> this.list = res.data.items).catch(err => console.error(err.message))
      }
}
}
</script>
<style>
</style>
