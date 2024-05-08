<template>
    <div id="nowplaying">
        <h1>Now Playing</h1>
        <h1 style="color: red;margin-bottom: 300px;" v-if="playingSong.song_id == 0">Please Pick a song</h1>
        <div v-if="!(playingSong.song_id == 0)">
            <img :src="require(`@/assets/${playingSong.image_url}`)" alt="(image)" style="width: 300px; height: 300px;object-fit: cover;"/>
            <h2>{{ playingSong.title }}</h2>
            <h3>{{ playingSong.artist }}</h3>
        </div>
        <div id="controls_bar">
            <div id="btn_back" class="button" @click="changeSong(-1)">
                <svg width="24px" height="24px" viewBox="0 0 24 24"
                    fill="none" xmlns="http://www.w3.org/2000/svg" color="#000000" stroke-width="1.5">
                    <path
                        d="M21.0441 5.70436C21.4402 5.41246 22 5.69531 22 6.1874V17.8126C22 18.3047 21.4402 18.5875 21.0441 18.2956L13.1555 12.483C12.8301 12.2432 12.8301 11.7568 13.1555 11.517L21.0441 5.70436Z"
                        fill="#000000" stroke="#000000" stroke-width="1.5" stroke-linecap="round"
                        stroke-linejoin="round"></path>
                    <path
                        d="M10.0441 5.70436C10.4402 5.41246 11 5.69531 11 6.1874V17.8126C11 18.3047 10.4402 18.5875 10.0441 18.2956L2.15555 12.483C1.8301 12.2432 1.8301 11.7568 2.15555 11.517L10.0441 5.70436Z"
                        fill="#000000" stroke="#000000" stroke-width="1.5" stroke-linecap="round"
                        stroke-linejoin="round"></path>
                </svg>
            </div>
            <div id="btn_play" class="button" @click="changeSong(0)">
                <svg width="24px" height="24px" viewBox="0 0 24 24"
                    fill="none" xmlns="http://www.w3.org/2000/svg" color="#000000" stroke-width="1.5">
                    <path
                        d="M6.90588 4.53682C6.50592 4.2998 6 4.58808 6 5.05299V18.947C6 19.4119 6.50592 19.7002 6.90588 19.4632L18.629 12.5162C19.0211 12.2838 19.0211 11.7162 18.629 11.4838L6.90588 4.53682Z"
                        fill="#000000" stroke="#000000" stroke-width="1.5" stroke-linecap="round"
                        stroke-linejoin="round"></path>
                </svg>
            </div>
            <div id="btn_next" class="button" @click="changeSong(1)">
                <svg width="24px" height="24px" viewBox="0 0 24 24"
                    fill="none" xmlns="http://www.w3.org/2000/svg" color="#000000" stroke-width="1.5">
                    <path
                        d="M2.95592 5.70436C2.55976 5.41246 2 5.69531 2 6.1874V17.8126C2 18.3047 2.55976 18.5875 2.95592 18.2956L10.8445 12.483C11.1699 12.2432 11.1699 11.7568 10.8445 11.517L2.95592 5.70436Z"
                        fill="#000000" stroke="#000000" stroke-width="1.5" stroke-linecap="round"
                        stroke-linejoin="round"></path>
                    <path
                        d="M13.9559 5.70436C13.5598 5.41246 13 5.69531 13 6.1874V17.8126C13 18.3047 13.5598 18.5875 13.9559 18.2956L21.8445 12.483C22.1699 12.2432 22.1699 11.7568 21.8445 11.517L13.9559 5.70436Z"
                        fill="#000000" stroke="#000000" stroke-width="1.5" stroke-linecap="round"
                        stroke-linejoin="round"></path>
                </svg>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'NowPlaying',
    data() {
        return {
            playingSong: {
                title: `unknown song`,
                artist: `unknown artist`,
                song_id: 0,
                image_url: "logo.png"
            },
        }
    },
    methods: {
        playSong: function (song) {
            this.playingSong = song
        },
        changeSong: function(change) {
            this.$root.$emit(`changeSong`, change);
        }
    },
    mounted() {
        this.$root.$on('choosePlaying', this.playSong)
    },
}
</script>
<style scoped>
.button {
    cursor: pointer;
    height: 60px;
    width: 60px;
    display: grid;
    justify-items: center;
    align-items: center;

    /* background-color: blue; */
}

#controls_bar {
    display: grid;
    grid-template-columns: auto auto auto;
    justify-items: center;
    width: 500px;
    margin-inline: auto;
}
</style>