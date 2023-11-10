<template>
  <div class="bigscreen">
    <div class="title">
      <div style="display: flex;padding-top: 10px;">
      <img :src="back" style="padding-right: 10px;margin-bottom: 10px;cursor: pointer;" @click="clickBack()" />
      <img :src="fullscreen" style="padding-right: 10px;margin-bottom: 10px;cursor: pointer;" @click="fullScreen()"/>
      <img :src="exitscreen" style="padding-right: 10px;margin-bottom: 10px;cursor: pointer;" @click="exitScreen()"/>
      </div>
    </div>
    <div class="maincontent" style="display: flex;align-self: center;justify-content: center;">
      <div class="mapcenter">
        <Map ref="mapChild"/>
      </div>
    </div>
  </div>
</template>

<script>
import Map from './components/Map.vue'
export default {
  name: 'bigscreen',
  components: {
    Map,
  },
  data() {
    return {

      back: require('./assets/back.svg'),
      exit: require('./assets/exit.svg'),
      exitscreen: require('./assets/exitscreen.svg'),
      fullscreen: require('./assets/fullscreen.svg'),
      startVal1: 0,
      endVal1: 805.34,
      startVal2: 0,
      endVal2: 124.34,
      startVal3: 0,
      endVal3: 213.34,
      startVal4: 0,
      endVal4: 45.34,
      timer: null
    }
  },
  mounted(){
    this.timer = setInterval(() => {
      this.endVal1 = this.endVal1 * 1
      this.endVal2 = this.endVal2 * 1
      this.endVal3 = this.endVal3 * 1
      this.endVal4 = this.endVal4 * 1
    }, 5000)
  },
  destroyed() {
    clearInterval(this.timer)
  },
  methods: {
    clickBack() {
      this.$refs.mapChild.clickBack();
    },
    fullScreen() {
      let element = document.documentElement;
      if (element.requestFullscreen) {
          element.requestFullscreen();
        } else if (element.webkitRequestFullScreen) {
          element.webkitRequestFullScreen();
        } else if (element.mozRequestFullScreen) {
          element.mozRequestFullScreen();
        } else if (element.msRequestFullscreen) {
          element.msRequestFullscreen();
        }
      
   
    },
    exitScreen() {
      if (document.exitFullscreen) {
          document.exitFullscreen();
        } else if (document.webkitCancelFullScreen) {
          document.webkitCancelFullScreen();
        } else if (document.mozCancelFullScreen) {
          document.mozCancelFullScreen();
        } else if (document.msExitFullscreen) {
          document.msExitFullscreen();
        }
     
    }

  }
}
</script>

<style scoped>
.bigscreen {
  display: flex;
  flex-direction: column;
  width: 100%;
  /* height: 100%; */
}
.title {
    height: 20%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.title-pic {
  width: 100%;
}
.maincontent {
  display: flex;
  flex-direction: row;
  width: 100%;
  /* height: 80%; */
}
.mapcenter {
  width: 80%;
}
.workinfo {
  color: white;
  height: 250px;
  width: 200px;
}
.todayinfo {
  color: white;
  height: 200px;
  width: 150px;
}
.left {
  display: flex;
  flex-direction: column;

  width: 300px;
    position: relative;
    left: 80px;
    margin-bottom: 5px;
}
.right {
    width: 300px;
    position: relative;
    right: 90px;
}
.infoshow {
  color: white;
  width: 100px;
  height: 100px;
}
</style>