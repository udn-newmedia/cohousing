<template>
  <div class="ReadEnd">
    <label class="label" @click.prevent>
      <input  class="label__checkbox" type="checkbox" :checked="isChecked" @click.prevent>
      <span class="label__text">
        <span class="label__check">
          <i class="fa fa-check icon" aria-hidden="true"></i>
        </span>
      </span>
    </label>
    <div class="EndText animated fadeInUp" v-show="isChecked">
      <hr>
      <p>你已看完所有貼文</p>
      <hr>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
  name: "ReadEnd",
  data () {
    return {
      videoSet: 0,
      isChecked: false
    }
  },
  watch: {
    countVideoSeted (val) {
      if (val === 4) {
        window.addEventListener('scroll', this.handle_scroll)
      }
    }
  },
  computed: {
    ...mapGetters([
      'countVideoSeted'
    ])
  },
  methods: {
    handle_scroll: function () {
      let currentH = window.scrollY
      if (currentH > $('.ReadEnd').offset().top - window.innerHeight * 0.9) {
        this.isChecked = true
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.ReadEnd {
  position: relative;
  z-index: 50;
  width: 100%;
  margin: 10px 0;
}
.EndText{
  margin-top: 12px;
  display: flex;
  position: relative;
  animation-delay: .3;
  p{
    margin: 0 8px;
  }
  hr{
    position: relative;
    top: -5px;
    flex: 1;
    border-color: #737070;
  }
}
.label__checkbox {
  display: none;
}
.label__check {
  display: inline-block;
  border-radius: 50%;
  border: 5px solid rgba(0,0,0,0.1);
  background: white;
  vertical-align: middle;
  margin: 0 auto;
  width: 75px;
  height: 75px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: border .3s ease;
  i.icon {
    opacity: 0.2;
    color: transparent;
    transition: opacity .3s .1s ease;
    -webkit-text-stroke: 3px rgba(0,0,0,.5);
    font-size: 36px;
  }
  &:hover {
    border: 5px solid rgba(0,0,0,0.2);
  }
}
.label__checkbox:checked + .label__text .label__check {
  animation: check 1s cubic-bezier(0.895, 0.030, 0.685, 0.220) forwards;
  .icon {
    opacity: 1;
    transform: scale(0);
    color: white;
    -webkit-text-stroke: 0;
    animation: icon .6s cubic-bezier(1.000, 0.008, 0.565, 1.650) .1s 1 forwards;
  }
}

@keyframes icon {
  from {
    opacity: 0;
    transform: scale(0.3);
  }
  to {
    opacity: 1;
    transform: scale(1)
  }
}

@keyframes check {
  0% {
    transform: scale(1);
    border-width: 5px;
  }
  10% {
    transform: scale(1);
    opacity: 0.1;
    background: rgba(0,0,0,0.2);
    border-width: 15px;
  }
  12% {
    transform: scale(1);
    opacity: 0.4;
    background: rgba(0,0,0,0.1);
    border-width: 0;
  }
  50% {
    transform: scale(1.25);
    background: #00d478;
    border: 0;
    opacity: 0.6;
  }
  100% {
    transform: scale(1.25);
    background: #00d478;
    border: 0;
    opacity: 1;
  }
}
</style>
