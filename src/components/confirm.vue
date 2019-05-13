<template>
  <transition name="slide">
    <div class="confirm" v-if="confirm.isShow">
      <div class="bg"></div>
      <div class="confirm-content">
        <div class="content-head">
          <i @click="close"></i>
        </div>
        <div class="content">
          <div class="content-text">
            <slot></slot>
          </div>
        </div>
        <div class="content-foot">
          <button class="foot-btn" @click="close">确定</button>
          <button class="foot-btn" @click="close">取消</button>
        </div>
      </div>
    </div>
  </transition>
</template>
<script>
export default {
  name: 'confirm',
  props: {
    confirm: Object
  },
  data() {
    return {
      isShow: true,
      time: 3000,
      content: '',
      direction: 'right',
      background: '',
      color: '#fff'
    }
  },
  methods: {
    close() {
      this.confirm.isShow = false
    }
  }
}
</script>
<style scoped>
.slide-enter-active,
.slide-leave-active {
  transition: opacity 0.3s;
}
.slide-enter,
.slide-leave-to {
  opacity: 0;
}
.confirm {
  position: fixed;
  left: 0;
  top: 0;
  z-index: 999999;
  width: 100%;
  height: 100%;
}
.bg {
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.2);
}
.confirm-content {
  display: flex;
  flex-direction: column;
  width: 320px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 1000000;
  box-shadow: 0px 1px 3px 0px #999999;
  border-radius: 10px;
}
.content-head {
  position: relative;
  width: 100%;
  height: 25px;
  background-color: #048754;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}
.content-head i:before {
  position: absolute;
  right: 15px;
  color: #fff;
  margin-left: 5px;
  font-style: normal;
  content: '\2716';
}
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  background-color: #fff;
  box-sizing: border-box;
}
.content-text {
  width: 90%;
}
.content-foot {
  padding: 10px 0;
  width: 100%;
  background-color: #fff;
  border-bottom-right-radius: 10px;
  border-bottom-left-radius: 10px;
}
.foot-btn {
  color: #fff;
  border: none;
  background-color: #048754;
  border-radius: 5px;
  padding: 5px 10px;
  margin-right: 10px;
}
</style>

