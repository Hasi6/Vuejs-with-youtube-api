<template>
  <div v-if="video" class="col-md-8">
      <div class="embed-responsive embed-responsive-16by9">
          <iframe
          class="embeded-responsive-item"
        height="362"
        :src="videoUrl"
      />
      </div>
    <div class="details">
      <h4>{{video.snippet.title}}</h4>
      <p>{{video.snippet.description}}</p>
      
    </div>
  </div>
</template>
<script>
export default {
  name: "Video_Details",
  props: {
    video: Object
  },
  
  computed: {
      videoUrl(){
          return `https://www.youtube.com/embed/${this.video.id.videoId}`
      }
  },
};
</script>

<style>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid black;
  border-radius: 4px;
}
</style> 