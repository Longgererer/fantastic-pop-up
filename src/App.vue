<template>
  <div id="app">
    <h2>弹窗</h2>
    <button id="openPop" @click="openPop">normal-pop</button><br />
    <button id="confirm" @click="openConfirm">confirm</button><br />
    <h2>提示</h2>
    <div class="btn-box">
      <button id="topInfo" @click="openInfo('infoConfigTop')">
        topInfo
        <info :infoConfig="infoConfigTop" type="top" /></button
      ><br />
      <button id="leftInfo" @click="openInfo('infoConfigLeft')">
        leftInfo
        <info :infoConfig="infoConfigLeft" type="left" />
      </button>
      <button id="rightInfo" @click="openInfo('infoConfigRight')">
        rightInfo
        <info :infoConfig="infoConfigRight" type="right" /></button
      ><br />
      <button id="bottomInfo" @click="openInfo('infoConfigBottom')">
        bottomInfo
        <info :infoConfig="infoConfigBottom" type="bottom" />
      </button>
    </div>
    <popUp :pop="pop">
      <h3>我是标题</h3>
      <p>
        这里是内容，这里是内容，这里是内容，这里是内容，这里是内容，这里是内容，这里是内容，这里是内容
      </p>
    </popUp>
    <confirm :confirm="confirm">
      <p>这里是提示，这里是提示，这里是提示</p>
    </confirm>
  </div>
</template>
<script>
import popUp from './components/popUp'
import confirm from './components/confirm'
import info from './components/info'
export default {
  name: 'App',
  data() {
    return {
      pop: {
        isShow: false
      },
      confirm: {
        isShow: false
      },
      infoConfigTop: {
        isShow: false,
        time: 3000,
        content: 'this is top info',
        background: 'rgba(0, 0, 0, .7)',
        color: '#fff'
      },
      infoConfigLeft: {
        isShow: false,
        time: 3000,
        content: 'this is left info',
        background: 'rgba(0, 0, 0, .7)',
        color: '#fff'
      },
      infoConfigRight: {
        isShow: false,
        time: 3000,
        content: 'this is right info',
        background: 'rgba(0, 0, 0, .7)',
        color: '#fff'
      },
      infoConfigBottom: {
        isShow: false,
        time: 3000,
        content: 'this is bottom info',
        background: 'rgba(0, 0, 0, .7)',
        color: '#fff'
      }
    }
  },
  components: {
    popUp,
    confirm,
    info
  },
  methods: {
    openPop() {
      this.pop.isShow = true
    },
    openConfirm() {
      this.confirm.isShow = true
    },
    openInfo(obj) {
      console.log(obj)
      this[obj].isShow = true
    }
  }
}
</script>
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#openPop,
#confirm,
#topInfo,
#leftInfo,
#bottomInfo,
#rightInfo {
  margin-top: 10px;
  color: #fff;
  background-color: #ffd700;
  border: none;
  padding: 8px;
  border-radius: 5px;
}
#topInfo,
#leftInfo,
#bottomInfo,
#rightInfo {
  outline: none;
  position: relative;
}
#openPop:hover,
#confirm:hover,
#topInfo:hover,
#leftInfo:hover,
#bottomInfo:hover,
#rightInfo:hover {
  background-color: #dab902;
}
.btn-box {
  margin: 50px 0;
}
</style>