<template>
  <div>
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
export default {
    name: 'AppHome'
}
</script>
