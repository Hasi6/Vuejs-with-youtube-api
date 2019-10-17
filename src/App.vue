<template>
  <div>
    <SearchBar @termChange="onTermChanged"></SearchBar>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar/SearchBar";
import axios from "axios";
const API_KEY = "AIzaSyDwSsXQ4V8GBH0PGfuAw9muk-_Y8d5hsjY";
const setKeyWord = async word => {
  try {
    
    const res = await axios.get(`https://www.googleapis.com/youtube/v3/search/`, {
      params: {
        key: API_KEY,
        type: "video",
        part: "snippet",
        q: word
      }
    });
    console.log(res)
  } catch (err) {
    console.error(err.message);
  }
};

export default {
  name: "app",
  components: {
    SearchBar
  },
  methods: {
    onTermChanged: word => setKeyWord(word)
  }
};
</script>
<style>
</style>
