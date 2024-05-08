<template>
    <div>
        <div class="song_wrapper">
            <h1>Playlist</h1>
            <div v-for="(song, index) in songs" v-bind:key="index"  @click="choosePlaying(index)">
                <div class="song_container" ref="song">
                    <span class="id">
                        {{ index + 1 }}
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
            songs: [],
            currentSong: 0,
        }
    },
    methods: {
        addSong: function(song){
            this.songs.push(song);
        },
        choosePlaying: function(index){
            // console.log('current song index is: ', index)
            this.$root.$emit(`choosePlaying`, this.songs[index]);
            this.currentSong = index;
            this.highlightBackground(index);
        },
        changePlaying: function(change){
            if(this.songs.length > 1){
                // console.log('changed song by', change, 'the current index will be', this.currentSong + change, 'there are _ songs in the list', this.songs.length)
                if(this.currentSong + change > -1 && this.currentSong + change <= (this.songs.length - 1)){
                    this.currentSong = this.currentSong + change;
                    this.choosePlaying(this.currentSong);
                }else if(this.currentSong + change < 0){
                    this.currentSong = this.songs.length - 1;
                    this.choosePlaying(this.currentSong);
                }else if(this.currentSong + change >= (this.songs.length - 1)){
                    this.currentSong = 0;
                    this.choosePlaying(this.currentSong);
                }
            }

        },
        highlightBackground: function(index) {
            // console.log(index)
            for(let i=0; i<this.$refs.song.length;i++){
                if(i == index){
                    this.$refs.song[i].style.backgroundColor = "lightgreen"
                }else{
                    this.$refs.song[i].style.backgroundColor = "white"
                }
            }
        }
    },
    mounted() {
        this.$root.$on('chooseSong', this.addSong)
        this.$root.$on('changeSong', this.changePlaying)
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