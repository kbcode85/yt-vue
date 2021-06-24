<template>
    <div v-if="video">
        <div class="ratio ratio-16x9">
            <iframe :src="videoUrl" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
        <div class="details">
            <h4>{{video.snippet.title}}</h4>
            <p>{{video.snippet.description}}</p>
        </div>
        
    </div>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: ['video'],
    computed: {
        videoUrl(){
            // const videoId = this.video.id.videoId
            const { videoId } = this.video.id
            return `https://www.youtube.com/embed/${videoId}`
        }
    }
}
</script>

<style scoped>
.details {
    margin-top: 10px;
    padding: 10px;
    border: 1px solid black;
    border-radius: 5px;
}
</style>