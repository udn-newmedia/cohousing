<template>
  <div class="carousel">
    <div class="carousel_wrapper">
      <div class="carousel_prev" @click="handle_nav_click(carouselIndex - 1, '左邊箭頭')">
        <i class="fa fa-angle-left fa-2x" aria-hidden="true"></i>
      </div>
      <div class="carousel_next" @click="handle_nav_click(carouselIndex + 1, '右邊箭頭')">
        <i class="fa fa-angle-right fa-2x" aria-hidden="true"></i>
      </div>
      <!-- <p class="page_hint" v-show="carouselIndex === 0 ? true : false">
        1/{{carouselMenu.length}}
      </p> -->
      <p class="page_hint" v-show="hintShow">1/{{carouselMenu.length}}</p>
      <ul :style="{transform: 'translate(' + carouselIndex * -100 + '%, 0)'}">
        <li v-for="item in carouselMenu" :key="item.id"><img :src="item.img" :alt="item.info" @touchstart.passive="handle_touch" @touchmove.passive="handle_touch" @touchend.passive="handle_touch"></li>
      </ul>
    </div>
    <div class="carousel_nav">
      <span v-for="(item, index) in carouselMenu" :key="item.id" :class="{ 'active': item.isActive }"
      @click="handle_nav_click(index, '點點')"></span>
    </div>
    <div class="carousel_heart" @click="handle_heart_click">
      <i class="fa fa-2x" :class="{'fa-heart': heartActive, 'fa-heart-o': !heartActive}" aria-hidden="true"></i>
    </div>
    <div class="carousel_info">
      <p>{{carouselMenu[carouselIndex].info}}</p>
    </div>
  </div>
</template>

<script>
import Utils from 'udn-newmedia-utils'
export default {
  name: 'Carousel',
  props: {
    carouselMenu: {
      type: Array
    }
  },
  data () {
    return {
      handle_hint: true,
      hintShow: true,
      carouselIndex: 0,
      heartActive: false,
      onTouch: false,
      currentTouchX: null
    }
  },
  methods: {
    handle_nav_click (index, from) {
      let theLength = this.carouselMenu.length
      if (index >= 0 && index < theLength) {
        for (let i = 0; i < theLength; i++) {
          this.carouselMenu[i].isActive = false
        }
        this.carouselIndex = index
        this.carouselMenu[this.carouselIndex].isActive = true
      }
      window.ga("send", {
        "hitType": "event",
        "eventCategory": "headbar",
        "eventAction": "click",
        "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [carousel]" + "[" + from + "點擊]"
      })
    },
    handle_heart_click () {
      this.heartActive === true ? this.heartActive = false : this.heartActive = true
      window.ga("send", {
        "hitType": "event",
        "eventCategory": "headbar",
        "eventAction": "click",
        "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [愛心點擊]"
      })
    },
    handle_touch (event) {
      switch (event.type) {
        case 'touchstart':
          this.onTouch = true
          this.currentTouchX = event.touches[0].screenX
          break
        case 'touchmove':
          if (this.onTouch) {
            switch (true) {
              case event.touches[0].screenX > this.currentTouchX + 75:
                if (this.carouselIndex > 0) {
                  this.handle_nav_click(this.carouselIndex - 1)
                  this.onTouch = false
                  window.ga("send", {
                    "hitType": "event",
                    "eventCategory": "headbar",
                    "eventAction": "click",
                    "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [carousel sweep left]"
                  })
                }
                break
              case event.touches[0].screenX < this.currentTouchX - 75:
                if (this.carouselIndex < this.carouselMenu.length) {
                  this.handle_nav_click(this.carouselIndex + 1)
                  this.onTouch = false
                  window.ga("send", {
                    "hitType": "event",
                    "eventCategory": "headbar",
                    "eventAction": "click",
                    "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [carousel sweep right]"
                  })
                }
            }
          }
          break
        case 'touchend':
          this.onTouch = false
      }
    },
    handle_scroll () {
      let currentH = window.scrollY
      const targetH = $(this.$el).offset().top - window.innerHeight * 0.8
      if (currentH > targetH && this.handle_hint) {
        this.handle_hint = false
        setTimeout(() => {
          this.hintShow = false
        }, 1888)
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handle_scroll)
  }
}
</script>

<style lang="scss" scoped>
.carousel{
  position: relative;
  z-index: 0;
  width: 100%;
}
.page_hint{
  position: absolute;
  z-index: 50;
  top: 10px;
  right: 12px;
  background-color: rgba(#000, .7);
  border-radius: 12px;
  padding: 0 8px;
  color: #fff;
  font-size: 14px;
  line-height: 1.8;
}
.carousel_wrapper{
  position: relative;
  width: 100%;
  overflow: hidden;
  ul{
    display: flex;
    align-items: center;
    width: 100%;
    padding-left: 0;
    margin-bottom: 0;
    transition: transform 666ms ease-out;
    &::before{
      content: '';
      padding-top: 100%;
      float: left;
    }
    &::after{
      content: '';
      display: block;
      clear: both;
    }
    li{
      position: relative;
      list-style: none;
      flex-shrink: 0;
      width: 100%;
      height: 100%;
      img{
        width: 100%;
        height: 100%;
      }
    }
  }
}
.carousel_nav{
  margin-top: 16px;
  width: 100%;
  height: 16px;
  display: flex;
  justify-content: center;
  align-items: center;
  span{
    width: 8px;
    height: 8px;
    cursor: pointer;
    background-color: #dadada;
    border-radius: 50%;
    margin-right: 8px;
    &:last-child{
      margin: 0;
    }
  }
  .active {
    background-color: #3c98ee;
  }
}
.carousel_heart{
  display: inline-block;
  position: relative;
  margin: 12px 0;
  cursor: pointer;
}
.carousel_info{
  color: #626262;
}
.fa-heart{
  color: #e93838 !important;
}
.carousel_prev, .carousel_next{
  display: none;
  @media screen and (min-width: 1025px) {
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
    position: absolute;
    z-index: 100;
    top: 50%;
    margin-top: -25px;
    height: 50px;
    width: 50px;
    color: #000;
    opacity: .6;
    background-color: #fff;
    box-shadow: 0 0 5px 2px rgba(124, 124, 124, 0.2);
    cursor: pointer;
    &:hover{
      opacity: 1;
    }
  }
}
.carousel_prev{
  left: 12px;
}
.carousel_next{
  right: 12px;
}
</style>
