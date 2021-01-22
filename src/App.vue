<template>
  <div id="app">
    <div class="pointer"><Timeline v-bind:timeline="timeline" /></div>
  </div>
</template>

<script>
import Timeline from "./components/Timeline.vue";
import timeline from "./timeline.json";

export default {
  name: "App",
  components: {
    Timeline
  },
  data() {
    return {
      timeline: timeline
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  position: relative;
  padding-top: 7em;
}

.pointer {
  position: absolute;
  width: 27em;
  top: 0;
  left: 30%;
}
</style>
