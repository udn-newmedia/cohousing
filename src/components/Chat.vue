<template>
  <div class="lineSection">
    <div class="line_chatcontent">
      <div class="compare" ref="compare">
        <div class="compare-item animated" :class="{'fadeInLeft': showCompare}">
          <img src="../../static/image_0812/meian.jpg" alt="陳玫安">
          <p style="margin-top: 10px;">陳玟安 20歲</p>
          <span>文化大學心輔系三年級<br/>入住陽明老人公寓5個月</span>
        </div>
        <div class="compare-item animated" :class="{'fadeInRight': showCompare}">
          <img src="../../static/image_0812/anna.jpg" alt="謝安娜">
          <p style="margin-top: 10px;">謝安娜 72歲</p>
          <span>入住陽明老人公寓3年</span>
        </div>
      </div>
      <span class="chatTime animated" ref="chatTime" :class="{'fadeInUp': showChatTime}">2018.07.09</span>
      <span class="greenbubble animated" ref="bubble_1" :class="{'fadeInUp': showChat_1}">明天晚上玩桌遊唷</span>
      <span class="greenbubble animated" ref="bubble_2" :class="{'fadeInUp': showChat_2}">奶奶要來玩嗎？</span>
      <span class="whitebubble animated" ref="bubble_3" :class="{'fadeInUp': showChat_3}">不是今天嗎？</span>
      <span class="greenbubble animated" ref="bubble_4" :class="{'fadeInUp': showChat_4}">最後決定是明天了！</span>
      <span class="greenbubble animated" ref="bubble_5" :class="{'fadeInUp': showChat_5}">昨天還不確定時間</span>
      <span class="greenbubble animated" ref="bubble_6" :class="{'fadeInUp': showChat_6}">412張爺爺提供3種桌遊</span>
      <span class="whitebubble animated" ref="bubble_7" :class="{'fadeInUp': showChat_7}">明晚幾點？</span>
      <span class="greenbubble animated" ref="bubble_8" :class="{'fadeInUp': showChat_8}">七點</span>
      <span class="whitebubble animated" ref="bubble_9" :class="{'fadeInUp': showChat_9}">好的我會來</span>
      <span class="greenbubble animated" ref="bubble_10" :class="{'fadeInUp': showChat_10}">太好了！非常歡迎</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Chat',
  data () {
    return {
      showCompare: false,
      showChatTime: false,
      showChat_1: false,
      showChat_2: false,
      showChat_3: false,
      showChat_4: false,
      showChat_5: false,
      showChat_6: false,
      showChat_7: false,
      showChat_8: false,
      showChat_9: false,
      showChat_10: false
    }
  },
  methods: {
    handle_scroll () {
      let currentH = window.pageYOffset
      const wH = window.innerHeight
      const ddd = 0.75
      switch (true) {
        case currentH > $(this.$refs.compare).offset().top - (wH * ddd) && !this.showCompare:
          this.showCompare = true
          break
        case currentH > $(this.$refs.chatTime).offset().top - (wH * ddd) && !this.showChatTime:
          this.showChatTime = true
          break
        case currentH > $(this.$refs.bubble_1).offset().top - (wH * ddd) && !this.showChat_1:
          this.showChat_1 = true
          break
        case currentH > $(this.$refs.bubble_2).offset().top - (wH * ddd) && !this.showChat_2:
          this.showChat_2 = true
          break
        case currentH > $(this.$refs.bubble_3).offset().top - (wH * ddd) && !this.showChat_3:
          this.showChat_3 = true
          break
        case currentH > $(this.$refs.bubble_4).offset().top - (wH * ddd) && !this.showChat_4:
          this.showChat_4 = true
          break
        case currentH > $(this.$refs.bubble_5).offset().top - (wH * ddd) && !this.showChat_5:
          this.showChat_5 = true
          break
        case currentH > $(this.$refs.bubble_6).offset().top - (wH * ddd) && !this.showChat_6:
          this.showChat_6 = true
          break
        case currentH > $(this.$refs.bubble_7).offset().top - (wH * ddd) && !this.showChat_7:
          this.showChat_7 = true
          break
        case currentH > $(this.$refs.bubble_8).offset().top - (wH * ddd) && !this.showChat_8:
          this.showChat_8 = true
          break
        case currentH > $(this.$refs.bubble_9).offset().top - (wH * ddd) && !this.showChat_9:
          this.showChat_9 = true
          break
        case currentH > $(this.$refs.bubble_10).offset().top - (wH * ddd) && !this.showChat_10:
          this.showChat_10 = true
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handle_scroll)
  }
}
</script>

<style lang="scss" scoped>
.animated{
  animation-duration: 2s !important;
  animation-timing-function: cubic-bezier(.23,1,.32,1) !important;
}
.lineSection{
  position: relative;
  z-index: 30;
  width: 100%;
  padding: 64px 15px;
  margin: 0 auto;
  background-color: transparent;
  overflow: hidden;
  @media (min-width: 768px) and (max-width: 1023px) {
    padding: 64px 100px;
  }
  @media screen and (min-width: 1024px) {
    padding: 84px 0;
  }
}
.line_chatcontent{
  position: relative;
  z-index: 30;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  @media screen and (min-width: 1024px) {
    width: 880px;
    margin: 0 auto;
  }
}
.compare{
  position: relative;
  width: 100%;
  display: flex;
  margin-bottom: 5vh;
  overflow: hidden;
}
.compare-item{
  width: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  opacity: 0;
  img{
    max-width: 150px;
    width: 60%;
    border-radius: 50%;
    overflow: hidden;
  }
  span{
    padding: 0 8px;
    font-size: 14px;
    @media screen and (max-width: 374px) {
      font-size: 13px;
    }
  }
}
.chatTime{
  opacity: 0;
  position: relative;
  z-index: 100;
  width: 130px;
  height: 14px;
  font-family: MicrosoftJhengHei;
  font-size: 14px;
  font-weight: normal;
  font-style: normal;
  font-stretch: normal;
  line-height: 1.61;
  letter-spacing: normal;
  text-align: center;
  color: #aaa9a9;
  padding: 10px;
  background-color: #f0f2f2;
  box-sizing: content-box;
}
.greenbubble{
  position: relative;
  margin-right: 15%;
  margin-top: 15px;
  border-radius: 35px;
  background-color: #b2ed8b;
  padding: 6px 22px;
  border: 15px solid #f0f2f2;
  opacity: 0;
}
.whitebubble{
  position: relative;
  margin-left: 15%;
  opacity: 0;
  margin-top: 15px;
  border-radius: 35px;
  background-color: #fff;
  padding: 6px 22px;
  border: 15px solid #f0f2f2;
}
</style>
