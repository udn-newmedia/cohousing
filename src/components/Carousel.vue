<template>
  <div class="carousel">
    <div class="carousel_wrapper">
      <p class="page_hint" v-show="carouselIndex === 0 ? true : false">
        1/{{carouselMenu.length}}
      </p>
      <ul :style="{transform: 'translate(' + carouselIndex * -100 + '%, 0)'}">
        <li v-for="item in carouselMenu" :key="item.id"><img :src="item.img" :alt="item.info"></li>
      </ul>
    </div>
    <div class="carousel_nav">
      <span v-for="(item, index) in carouselMenu" :key="item.id" :class="{ 'active': item.isActive }"
      @click="handle_nav_click(index)"></span>
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
// import _debounce from 'lodash.debounce'
// import Utils from 'udn-newmedia-utils'
export default {
  name: 'Carousel',
  props: {
    carouselMenu: {
      type: Array
    }
  },
  data () {
    return {
      carouselIndex: 0,
      heartActive: false
    }
  },
  methods: {
    handle_nav_click (index) {
      let theLength = this.carouselMenu.length
      for (let i = 0; i < theLength; i++) {
        this.carouselMenu[i].isActive = false
      }
      this.carouselMenu[index].isActive = true
      this.carouselIndex = index
    },
    handle_heart_click () {
      this.heartActive === true ? this.heartActive = false : this.heartActive = true
    }
  },
  mounted () {

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
    margin-bottom: 10px;
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
.fa-heart{
  color: #e93838 !important;
}
</style>
