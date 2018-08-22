<template>
  <div class="FixLineList" :class="{'closeLineList': !isListOpen}" :style="{opacity: isOpacity}">
    <div class="mask" :class="{'maskOut': isOpacity}" style="background-image: url('@/../static/image_0812/mask.png')"></div>
    <div class="LineList-item" v-for="item in peopleList" :key="item.id" @click="handle_click(item.id, item.name)">
      <img :src="item.img" :alt="item.name">
      <p>{{item.name}}</p>
    </div>
    <div class="toggle-btn" @click="handle_toggle">
      <i class="fa fa-1x" :class="{'fa-chevron-down': !isListOpen, 'fa-chevron-up': isListOpen}" aria-hidden="true"></i>
    </div>
  </div>
</template>

<script>
import Utils from 'udn-newmedia-utils'
export default {
  name: 'FixLineList',
  data () {
    return {
      hasShow: false,
      isOpacity: 0,
      isListOpen: false,
      // stickyHeight: 0,
      peopleList: [
        {
          id: 'ppl_1',
          name: '陳玟安',
          img: '@/../static/image_0812/meian.jpg'
        },
        {
          id: 'ppl_2',
          name: '謝安娜',
          img: '@/../static/image_0812/anna.jpg'
        },
        {
          id: 'ppl_3',
          name: '王斯特',
          img: '@/../static/image_0812/ster.jpg'
        },
        {
          id: 'ppl_4',
          name: '林育甄',
          img: '@/../static/image_0812/yuzen.jpg'
        }
      ]
    }
  },
  methods: {
    handle_toggle () {
      this.isListOpen === true
        ? this.isListOpen = false
        : this.isListOpen = true
    },
    handle_click (target, who) {
      $('html, body').animate({scrollTop: $('#' + target).offset().top - 96 + 'px'})
      if (window.innerWidth < 1025) {
        this.handle_toggle()
      }
      window.ga("send", {
        "hitType": "event",
        "eventCategory": "headbar",
        "eventAction": "click",
        "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [上方錨點]" + "[" + who + "點擊]"
      })
    },
    handle_scroll () {
      let currentH = window.pageYOffset
      if (window.innerWidth < 1025) {
        switch (true) {
          case currentH > $('#linePaper').offset().top && !this.hasShow:
            this.hasShow = true
            this.isOpacity = 1
            this.isListOpen = true
            break
          case currentH > 2:
            this.isOpacity = 1
            break
          case currentH < 2:
            this.isOpacity = 0
        }
      } else {
        if (currentH > $('#linePaper').offset().top - 120 && currentH < $('.ReadEnd').eq(0).offset().top) {
          this.isOpacity = 1
        } else {
          this.isOpacity = 0
        }
      }
    }
  },
  created () {
    window.innerWidth < 1025
      ? this.isListOpen = false
      : this.isListOpen = true
  },
  mounted () {
    window.addEventListener('scroll', this.handle_scroll)
  }
}
</script>

<style lang="scss" scoped>
.FixLineList{
  position: fixed;
  z-index: 100;
  top: 48px;
  right: 0;
  overflow: hidden;
  width: 100%;
  padding: 12.5px 8px 25px 8px;
  display: flex;
  justify-content: flex-start;
  background-color: #fff;
  transition: transform 444ms;
  @media screen and (min-width: 1025px) {
    position: fixed;
    z-index: 0;
    top: 96px;
    right: 50%;
    width: 40%;
    flex-direction: column;
    max-width: 220px;
    background-color: transparent;
    padding: 0;
    transition: opacity 888ms;
    transform: translate(200%, 0);
    border-top: solid 1px #e6e6e6;
    padding-top: 20px;
  }
}
.mask{
  position: absolute;
  z-index: 100;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-size: 100% auto;;
  background-repeat: repeat;
  transition: transform 444ms;
}
.maskOut{
  transform: translate(0, 100%);
}
.toggle-btn{
  position: absolute;
  bottom: 0;
  left: 50%;
  margin-left: -8px;
  z-index: 100;
  cursor: pointer;
  @media screen and (min-width: 1025px) {
    display: none;
  }
}
.fa-chevron-up{
  color: #aaa9a9;
}
.LineList-item{
  height: 75px;
  border-radius: 50%;
  margin-right: 12px;
  display: flex;
  align-items: center;
  flex-direction: column;
  cursor: pointer;
  p{
    font-size: 12px;
    margin-bottom: 0;
    @media screen and (min-width: 1025px) {
      margin-left: 15px;
    }
  }
  img{
    border-radius: 50%;
    width: 55px;
    height: 55px;
  }
  @media screen and (min-width: 1025px) {
    flex-direction: row;
  }
}
.closeLineList{
  transform: translate(0, -80%);
}
</style>
