<template>
    <div class="recent-songs-sidebar">
        <h3>Últimas Canciones Reproducidas</h3>
        <ul>
            <li v-for="(song, index) in recentSongs" :key="index" @click="playRecentSong(song)">
                <img :src="song.images.spectral_m" alt="song image" />
                <span>{{ song.name }}</span>
            </li>
        </ul>
    </div>
</template>

<script setup>
import { computed } from 'vue';
import { useSoundDataStore } from '../stores/soundData';

const soundDataStore = useSoundDataStore();
const recentSongs = computed(() => soundDataStore.recentSongs);

const playRecentSong = (song) => {
    soundDataStore.soundName = song.name;
    soundDataStore.soundImg = song.images.spectral_m;
    soundDataStore.soundUrl = song.previews["preview-hq-mp3"];
};
</script>