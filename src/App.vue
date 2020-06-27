<template>
    <div id="app">
        <videoMain :end-time="data.end" :poster="data.poster" :set-time-value="data.setTimeValue" :source-data="data.video_link" :start-time="data.start" aspect-ratio="16:9" />

        <!-- <videoMain :poster="data.poster" :setTimeValue="data.setTimeValue" :sourceData="data.video_link" aspectRatio="16:9">
                <template v-for="(value, index) in data.setTimeValue">
                    <div :key="index">
                        <button @click="playVideo">
                            <span>Reproducir: {{ value.start }} - {{ value.end }}</span>
                        </button>
                    </div>
                </template>
        </videoMain>-->
    </div>
</template>

<script>
import videoMain from './components/videoMain.vue'

export default {
    name: 'App',
    components: {
        videoMain
    },
    data() {
        return {
            data: {
                id: 18,
                name: 'video_name',
                description: 'video_description',
                date: '2020-05-27T07:39:38.000Z',
                related_to: 'Competitions',
                video_type: 'Full Match',
                season: '2018-2019',
                competition_name: 'Premiere League 2018-2019',
                game_id: 1,
                video_link: [
                    {
                        src: 'https://videos-adc.s3.amazonaws.com/GMT20200425-000626_Mejorando-_1600x800.mp4',
                        type: 'video/mp4',
                        label: '480P'
                    },
                    {
                        src: 'https://videos-adc.s3.amazonaws.com/GMT20200425-000626_Mejorando-_1600x800.mp4',
                        type: 'video/mp4',
                        label: '720P'
                    },
                    {
                        src: 'https://videos-adc.s3.amazonaws.com/GMT20200425-000626_Mejorando-_1600x800.mp4',
                        type: 'video/mp4',
                        label: '1080P'
                    }
                ],
                setTimeValue: [
                    { start: 120, end: 240 },
                    { start: 240, end: 320 },
                    { start: 320, end: 480 },
                    { start: 480, end: 520 }
                ],
                // start: 60,
                // end: 120,
                poster: 'https://worldsoccertalk.com/wp-content/uploads/2014/11/scotland-england.jpg',
                keywords: '#liverpool =fullmatch !1280x720'
            }
        }
    },
    methods: {
        async playVideo() {
            this.player.offset({
                start: this.startTime,
                end: this.endTime,
                restart_beginning: false
            })
            this.player.reset()
            this.player.src(this.sourceData)
            await this.player.play()
            console.log('The video runs correct!')
            console.log(this.player.reset(), 'Reset method')
            console.log(this.player.src(this.sourceData), 'Source data init')
            console.log(this.player.play(), 'Play action')
        }
    }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
