<template>
    <li class="list-group-item media" @click="onVideoSelect">
        <img class="mr-3" :src="thumbnailUrl" alt="">
        <div class="media-body">
            {{video.snippet.title}}
        </div>
    </li>
</template>

<script>
export default {
    name: 'Video_List_Item',
    props: {
        video:Object
    },
    methods: {
        onVideoSelect(){
            this.$emit('videoSelect', this.video)
        }
    },
    computed: {
        thumbnailUrl(){
            return this.video.snippet.thumbnails.default.url
        }
    },
}
</script>

<style scoped>
    li{
        display: flex;
        cursor: pointer;
    }
    li:hover{
        background: #eee
    }
</style>