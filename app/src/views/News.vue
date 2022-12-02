<template>
  <div class="OverlayPage d-flex flex-column">
    <div class="liveHeader">
      <div class="liveLogo mt-16">
        <h3>{{ newsPage.liveText }}</h3>
      </div>

      <div class="liveClock">
        <h3>{{ this.time }}</h3>
      </div>
    </div>

    <v-spacer />
    <div class="news-header">{{ newsPage.headerText }}</div>
    <div class="ticker-wrap">
      <div class="ticker">
        <span
          v-for="(item, index) in newsPage.bottomTexts"
          :key="index"
          class="ticker-item"
          >{{ item.text }}</span
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["newsPage"],
  name: "News",
  components: {},
  data() {
    return {
      interval: null,
      time: null,
    };
  },

  beforeDestroy() {
    clearInterval(this.interval);
  },
  created() {
    this.interval = setInterval(() => {
      this.time = Intl.DateTimeFormat(navigator.language, {
        hour: "numeric",
        minute: "numeric",
        second: "numeric",
      }).format();
    }, 1000);
  },
};
</script>

<style>
.news-header {
  width: 100%;
  background: linear-gradient(
    90deg,
    rgba(43, 0, 0, 1) 0%,
    rgba(121, 9, 9, 1) 100%
  );
  min-height: 4rem;
  display: flex;
  align-items: center;
  color: white;
  font-weight: 800;
  font-size: 1.5rem;
  padding: 0 100px;
}
@-webkit-keyframes ticker {
  0% {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    visibility: visible;
  }
  100% {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
  }
}
@keyframes ticker {
  0% {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    visibility: visible;
  }
  100% {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
  }
}
.ticker-wrap {
  width: 100%;
  overflow: hidden;
  height: 2rem;
  background-color: rgba(202, 0, 0, 0.9);
  padding-left: 100%;
  box-sizing: content-box;
}
.ticker-wrap .ticker {
  display: inline-block;
  min-height: 2rem;
  line-height: 2rem;
  white-space: nowrap;
  padding-right: 100%;
  box-sizing: content-box;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  animation-name: ticker;
  animation-duration: 45s;
}

.ticker-wrap .ticker-item {
  padding: 0 2rem;
  font-size: 1.25rem;
  color: white;
}

.liveHeader {
  width: fit-content;
  min-width: 250px;
}

.liveHeader > div {
  padding-right: 12px;
}

.liveLogo {
  background: rgb(43, 0, 0);
  background: linear-gradient(
    90deg,
    rgba(43, 0, 0, 1) 0%,
    rgba(121, 9, 9, 1) 100%
  );
  color: white;
  text-align: right;
  width: 100%;
}

.liveClock {
  background-color: white;
  color: black;
  text-align: right;
  width: 100%;
}
</style>
