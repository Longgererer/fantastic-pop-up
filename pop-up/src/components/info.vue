<template>
  <transition name="slide">
    <div class="info" :class="type" :style="model" v-if="infoConfig.isShow">
      {{ infoConfig.content }}
    </div>
  </transition>
</template>

<script>
export default {
  name: 'info',
  props: {
    infoConfig: Object,
    type: String
  },
  data() {
    return {}
  },
  computed: {
    model() {
      const config = this.infoConfig
      return {
        backgroundColor: config.background,
        color: config.color
      }
    }
  },
  watch: {
    'infoConfig.isShow': function(newVal, oldVal) {
      if (newVal) {
        this.hidden()
      }
    }
  },
  methods: {
    hidden() {
      setTimeout(() => {
        this.infoConfig.isShow = false
      }, this.infoConfig.time)
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
.info {
  z-index: 100000;
  justify-content: center;
  position: absolute;
  border-radius: 5px;
  padding: 5px 10px;
  white-space: nowrap;
}
.top {
  top: -120%;
  left: 50%;
  transform: translate(-50%, 0);
}
.top:before {
  content: '';
  border-style: solid;
  border-width: 8px 8px 0 8px;
  border-color: #000 transparent transparent transparent;
  position: absolute;
  left: 50%;
  bottom: -8px;
  opacity: 0.7;
  transform: translate(-50%, 0);
}
.left {
  top: 50%;
  transform: translate(0, -50%);
  right: 120%;
}
.left:before {
  content: '';
  border-style: solid;
  border-width: 8px 0 8px 8px;
  border-color: transparent transparent transparent #000;
  position: absolute;
  opacity: 0.7;
  right: -8px;
}
.right {
  top: 50%;
  transform: translate(0, -50%);
  left: 120%;
}
.right:before {
  content: '';
  border-style: solid;
  border-width: 8px 8px 8px 0px;
  border-color: transparent #000 transparent transparent;
  position: absolute;
  opacity: 0.7;
  left: -8px;
}
.bottom {
  top: 140%;
  transform: translate(-50%, 0);
  left: 50%;
}
.bottom:before {
  content: '';
  border-style: solid;
  border-width: 0px 8px 8px 8px;
  border-color: transparent transparent #000 transparent;
  position: absolute;
  opacity: 0.7;
  top: -8px;
  left: 50%;
  transform: translate(-50%, 0);
}
</style>
