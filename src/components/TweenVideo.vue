<template>
  <div class="TweenVideo">
    <div class="videoWrapper">
      <video :src="src" :poster="poster" preload="metadata" autoplay playsinline :muted="muted" ref="TheVideo"
      @click="handle_video_play" @canplay="handle_canplay" @playing="handle_playing" @ended="handle_ended"></video>
    </div>
    <div class="volume_box" :class="{'notice': muted}" @click.stop="handle_volume_click">
      <i class="fa fa-2x" :class="{'fa-volume-up': !muted, 'fa-volume-off': muted}" aria-hidden="true"></i>
    </div>
  </div>
</template>

<script>
import Utils from 'udn-newmedia-utils'
import { mapActions } from 'vuex'
export default {
  name: 'TweenVideo',
  props: {
    src: {
      type: String
    },
    poster: {
      type: String
    }
  },
  data () {
    return {
      forcePause: false,
      muted: true,
      InterVal: null
    }
  },
  methods: {
    ...mapActions([
      'addVideoSet'
    ]),
    handle_volume_click () {
      if (this.muted) {
        this.muted = false
        this.$refs.TheVideo.play()
      } else {
        this.muted = true
      }
      window.ga("send", {
        "hitType": "event",
        "eventCategory": "headbar",
        "eventAction": "click",
        "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [聲音點擊]"
      })
    },
    handle_video_play () {
      if (this.$refs.TheVideo.paused) {
        this.$refs.TheVideo.play()
        this.forcePause = false
      } else {
        this.$refs.TheVideo.pause()
        this.forcePause = true
        clearInterval(this.InterVal)
      }
    },
    handle_scroll () {
      let currentH = window.pageYOffset
      let target = $(this.$el).offset().top - window.innerHeight * 0.75
      if (currentH > target && currentH < $(this.$el).offset().top + this.$el.clientHeight && !this.forcePause) {
        this.$refs.TheVideo.play()
      } else {
        this.$refs.TheVideo.pause()
        clearInterval(this.InterVal)
      }
    },
    handle_canplay () {
      this.addVideoSet()
    },
    handle_playing () {
      window.ga("send", {
        "hitType": "event",
        "eventCategory": "headbar",
        "eventAction": "click",
        "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [" + this.src + "] " + "[觀看 " + Math.floor(this.$refs.TheVideo.currentTime) + " 秒] [共" + Math.floor(this.$refs.TheVideo.duration) + "秒]"
      })
      this.InterVal = setInterval(() => {
        window.ga("send", {
          "hitType": "event",
          "eventCategory": "headbar",
          "eventAction": "click",
          "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [" + this.src + "] " + "[觀看 " + Math.floor(this.$refs.TheVideo.currentTime) + " 秒] [共" + Math.floor(this.$refs.TheVideo.duration) + "秒]"
        })
      }, 5000)
    },
    handle_ended (event) {
      clearInterval(this.InterVal)
      window.ga("send", {
        "hitType": "event",
        "eventCategory": "headbar",
        "eventAction": "click",
        "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [" + this.src + "] " + "[觀看 " + Math.floor(this.$refs.TheVideo.currentTime) + " 秒] [共" + Math.floor(this.$refs.TheVideo.duration) + "秒]"
      })
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handle_scroll)
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
}
.videoWrapper{
  position: relative;
  z-index: 50;
  width: 100%;
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
  box-shadow: 0px 0px 20px 5px rgba(#fff,1);
}
@keyframes volume_notice{
  0%{
    box-shadow: 0px 0px 20px 5px rgba(#fff,1);
  }
  50%{
    box-shadow: 0px 0px 20px 5px rgba(#fff,.5);
  }
  100%{
    box-shadow: 0px 0px 20px 5px rgba(#fff,.2);
  }
}
</style>
