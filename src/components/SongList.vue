<template>
    <div id="list_container">
        <div class="song_wrapper">
            <div v-for="song in songs" v-bind:key="song.song_id" @click="chooseSong(song.song_id)">
                <div class="song_container" ref="song" @mouseover="songBackground(song.song_id, true)"
                    @mouseleave="songBackground(song.song_id, false)">
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
    name: 'SongList',
    data() {
        return {
            songs: [
                {
                    title: `song a`,
                    artist: `artist a`,
                    song_id: 1,
                    image_url: "music2.png"
                }, {
                    title: `song b`,
                    artist: `artist b`,
                    song_id: 2,
                    image_url: "music.png"
                }, {
                    title: `song c`,
                    artist: `artist c`,
                    song_id: 3,
                    image_url: "music2.png"
                }, {
                    title: `song d`,
                    artist: `artist d`,
                    song_id: 4,
                    image_url: "logo.png"
                }, {
                    title: `song e`,
                    artist: `artist e`,
                    song_id: 5,
                    image_url: "music.png"
                },
                {
                    title: `song f`,
                    artist: `artist f`,
                    song_id: 6,
                    image_url: "music2.png"
                }, {
                    title: `song g`,
                    artist: `artist g`,
                    song_id: 7,
                    image_url: "music.png"
                }, {
                    title: `song h`,
                    artist: `artist h`,
                    song_id: 8,
                    image_url: "music2.png"
                }, {
                    title: `song i`,
                    artist: `artist i`,
                    song_id: 9,
                    image_url: "logo.png"
                }, {
                    title: `song j`,
                    artist: `artist j`,
                    song_id: 10,
                    image_url: "music.png"
                },
            ]
        }
    },
    methods: {
        chooseSong: function (song) {
            this.$emit(`chooseSong`, this.songs[song - 1])
        },
        songBackground: function (song, highlight) {
            if (highlight) {
                this.$refs.song[song - 1].style.backgroundColor = "lightgray"
            } else {
                this.$refs.song[song - 1].style.backgroundColor = "white"
            }
        }
    },
}
</script>
<style scoped>
* {
    box-sizing: border-box;
}

#list_container {
    border: 1px black solid;
    height: 260px;
    overflow: auto;
    scrollbar-color: transparent transparent;
    scrollbar-width: 0px;
    text-align: start;
    margin-top: 50px;
}

.song_wrapper{
    width: 1000px;
    margin-inline: auto;
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