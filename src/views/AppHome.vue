<template>
  <div>
    <VideoPlayer
      :source-data="data.video_link"
      :start-time="data.start"
      :end-time="data.end"
      :poster="data.poster"
      :set-time-value="data.setTimeValue"
      aspect-ratio="16:9"
    />
  </div>
</template>

<script>
import VideoPlayer from '@/components/VideoPlayer.vue'
export default {
	name: 'AppHome',
	components: { VideoPlayer },
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
				poster: 'https://worldsoccertalk.com/wp-content/uploads/2014/11/scotland-england.jpg',
				keywords: '#liverpool =fullmatch !1280x720'
			}
		}
	}
}
</script>
