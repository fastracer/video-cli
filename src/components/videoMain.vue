<template>
    <!-- <div>
        <div class="video-tool">
            <video class="video-js" ref="videoPlayer" />
            <slot />
        </div>
        <template v-for="(value, index) in setTimeValue">
            <div :key="index">
                <button @click="playVideo">
                    <span>Reproducir: {{ value.start }} - {{ value.end }}</span>
                </button>
            </div>
        </template>
        <pre>{{ setTimeValue.start }}</pre>
        <pre>{{ setTimeValue.end }}</pre>
    </div>-->
    <div>
        <div class="video-tool">
            <video class="video-js" ref="videoPlayer"></video>
        </div>
        <div>
            <span>
                Reproducir start: {{ startTime }} - End: {{ endTime }}
                <button @click="playVideo">Reproducir</button>
            </span>
        </div>
        <pre>Set Time Value: {{ setTimeValue }}</pre>
        <pre>Source video: {{ sourceData }}</pre>
        <pre>Start: {{ startTime }}</pre>
        <pre>End: {{ endTime }}</pre>
    </div>
</template>

<script>
import videojs from "video.js";
import offset from "videojs-offset/dist/videojs-offset";
import "video.js/dist/video-js.css";

export default {
    name: "VideoTool",

    props: {
        setTimeValue: { type: Array, required: false },
        // aspectRatio: { type: String, required: true },
        // poster: { type: String, required: true },
        // sourceData: { type: Array, required: true }

        aspectRatio: { type: String, required: true },
        endTime: { type: Number, required: false },
        poster: { type: String, required: true },
        sourceData: { type: Array, required: true },
        startTime: { type: Number, required: false }
    },

    data() {
        return {
            player: null,
            options: {
                aspectRatio: this.aspectRatio,
                playbackRates: [0.5, 1.0, 1.5, 2.0],
                autoplay: false,
                controls: true,
                controlBar: {
                    children: [
                        "playToggle",
                        "volumePanel",
                        "playbackRateMenuButton",
                        "progressControl",
                        "remainingTimeDisplay",
                        "fullscreenToggle"
                    ],
                    pictureInPictureToggle: true,
                    volumePanel: {
                        inline: false
                    }
                },
                poster: this.poster,
                preload: "auto",
                fluid: true,
                sources: this.sourceData
            }
        };
    },

    methods: {
        async playVideo() {
            this.player.offset({
                start: this.setTimeValue[0].start,
                end: this.setTimeValue[0].end,
                // start: this.startTime,
                // end: this.endTime,
                restart_beginning: false
            });
            this.player.reset();
            this.player.src(this.sourceData);
            await this.player.play();
        }
    },

    mounted() {
        this.player = videojs(this.$refs.videoPlayer, this.options);
        console.log(this.setTimeValue);
    },

    beforeDestroy() {
        if (this.player) {
            this.player.dispose();
        }
    }
};
</script>

<style>
.video-js .vjs-big-play-button {
    border-radius: 50%;
    border: none;
    font-size: 36px;
    height: 80px;
    left: 50%;
    line-height: 2.2;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 80px;
}

.video-js .vjs-control-bar {
    background: #000;
    margin-bottom: 20px;
}

.vjs-menu li.vjs-selected {
    background: #000;
    color: #fff;
    padding-bottom: 5px;
    padding-top: 5px;
}
</style>