<template>
    <div>
        <div class="song_wrapper">
            <h1>Playlist</h1>
            <div v-for="song in songs" v-bind:key="song.song_id"  @click="chooseSong(song.song_id)">
                <div class="song_container" ref="song">
                    <span class="id">
                        {{ song.song_id }}
                    </span>
                    <span class="title">
                        {{ song.title }}
                    </span>
                    <span class="artist">
                        {{ song.artist }}
                    </span>
                </div>
            </div>

        </div>
    </div>
</template>
<script>
export default {
    name: 'PlayList',
    data() {
        return {
            songs: []
        }
    },
    methods: {
        addSong: function(song){
            this.songs.push(song);
        }
    },
    mounted() {
        this.$root.$on('chooseSong', this.addSong)
    },
    
}
</script>
<style scoped>
.song_wrapper{
    margin-top: 100px;
    padding-bottom: 60px;
    width: 1000px;
    margin-inline: auto;
    border: 1px solid blue;
}
.song_container {
    padding-top: 15px;
    padding-left: 200px;
    margin-top: 5px;
    cursor: pointer;

    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    justify-items: start;
}

.title {
    font-weight: bolder;

}

.artist {
    color: darkgray;
    font-style: italic;

}
</style>