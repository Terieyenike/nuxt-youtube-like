<template>
  <div>
    <div class="relative">
    <video id="doc-player" ref="video" muted class="cld-video-player cld-fluid" @click.prevent="unmuteVideo"></video>

    <button @click.prevent="unmuteVideo" ref="text" class="absolute bg-blue-700 text-white top-0 left-0 px-3 py-2">Unmute</button>

    </div>
  </div>
</template>


<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      player: null,
      videoId: 'video-player/early_morning'
    }
  },
  methods: {
    unmuteVideo() {
      const vid = this.$refs.video
      if (!vid.muted) {
        this.$refs.text.textContent = "Unmute"

      } else {
        this.$refs.text.textContent = "Mute"
      }
      vid.muted = !vid.muted
    }
  },
  mounted() {
    this.player = cloudinary.videoPlayer('doc-player', {
      cloud_name: 'terieyenike',
      autoplay: true,
      controls: true
    })
    this.player.source(this.videoId)
  }
}
</script>
