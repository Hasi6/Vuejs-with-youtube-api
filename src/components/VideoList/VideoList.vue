<template>
<ul>
    <li v-for="lis in list" :key="lis.id">
        {{lis.etag}}
    </li>
</ul>
</template>

<script>
// import VideoListItem from './VideoListItem/VideoListItem'
export default {
    name: 'VideoList',
    components: {
        // VideoListItem
    },
    props: {
        list: Array
    },
    
}
</script>

<style>
    
</style>