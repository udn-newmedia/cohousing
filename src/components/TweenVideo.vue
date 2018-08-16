<template>
  <div class="TweenVideo">
    <video :src="src" preload="metadata" playsinline :muted="muted" ref="TheVideo"
    @click="handle_video_play" @canplay="handle_canplay"></video>
    <div class="volume_box" :class="{'notice': muted}" @click="handle_volume_click">
      <i class="fa fa-2x" :class="{'fa-volume-up': !muted, 'fa-volume-off': muted}" aria-hidden="true"></i>
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
  name: 'TweenVideo',
  props: {
    src: {
      type: String
    }
  },
  data () {
    return {
      muted: true
    }
  },
  methods: {
    ...mapActions([
      'addVideoSet'
    ]),
    handle_volume_click () {
      this.muted === true
        ? this.muted = false
        : this.muted = true
    },
    handle_video_play (event) {
      if (event.target.paused) {
        event.target.play()
      } else {
        event.target.pause()
      }
    },
    handle_scroll () {
      let currentH = window.pageYOffset
      let target = $(this.$el).offset().top - 60
      if (currentH > target && currentH < target + this.$el.clientHeight) {
        this.$refs.TheVideo.play()
      } else {
        this.$refs.TheVideo.pause()
      }
    },
    handle_canplay () {
      this.addVideoSet()
      window.addEventListener('scroll', this.handle_scroll)
    }
  }
}
</script>

<style lang="scss" scoped>
.TweenVideo{
  position: relative;
  z-index: 50;
  width: 100%;
  background-color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  video{
    width: 100%;
  }
  video::-internal-media-controls-download-button {
      display:none;
  }

  video::-webkit-media-controls-enclosure {
      overflow:hidden;
  }
  video::-webkit-media-controls-panel {
      width: calc(100% + 30px); /* Adjust as needed */
  }
}
.volume_box{
  display: flex;
  align-items: center;
  justify-content: center;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: rgba(#000, .7);
  position: absolute;
  z-index: 100;
  left: 15px;
  bottom: 15px;
  color: #fff;
  cursor: pointer;
}
.notice{
  animation: volume_notice 888ms alternate infinite ease-out;
  box-shadow: 0px 0px 50px 15px rgba(255,213,0,1);
}
@keyframes volume_notice{
  0%{
    box-shadow: 0px 0px 50px 15px rgba(255,213,0,1);
  }
  50%{
    box-shadow: 0px 0px 50px 15px rgba(255,213,0,.5);
  }
  100%{
    box-shadow: 0px 0px 50px 15px rgba(255,213,0,.2);
  }
}
</style>
