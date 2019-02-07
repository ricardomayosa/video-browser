<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div class="row">
            <VideoDetail :video="selectedVideo"></VideoDetail>
            <!-- <VideoList v-on:videoSelect="onVideoSelect" v-bind:videos="videos"></VideoList> -->
            <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
        </div>
        
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail'
//  Llave del proyecto 'My Project 85298'
// const API_KEY = 'AIzaSyC0fYPwOeyWu6AP0SpkfwzVv-l1F8YyffI';
const API_KEY = 'AIzaSyA6uEKUY8ZDUM3cIzDpXbDLgUozCOBBbm4';
export default {
    name: 'App',
    data() {
        return {
            videos: [],
            selectedVideo: null,
        }
    },
    components: {
        SearchBar,
        VideoList,
        VideoDetail
    },
    methods: {
        onTermChange(searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            })
            .then(res => {
                this.videos = res.data.items;
                
            })
            .catch()
        },
        onVideoSelect(video) {
            this.selectedVideo = video;
        }
    }
}
</script>
