<template>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    :viewBox="'-80 0 350 ' + 80 * timeline.length"
  >
    <circle cx="80" cy="10" r="8" fill="blue" stroke="blue" stroke-width="4" />
    <line x1="80" y1="20" x2="80" y2="70" style="stroke:blue;stroke-width:7" />
    <g
      v-for="(item, index) in timeline"
      :key="item.message"
      transform="translate(0, 70)"
    >
      <line
        x1="80"
        :y1="20 * index"
        x2="80"
        :y2="70 * index"
        style="stroke:blue;stroke-width:7"
      />
      <g v-if="index % 2 == 0" :transform="'translate(60,' + index * 70 + ')'">
        <circle
          cx="20"
          cy="10"
          r="8"
          fill="blue"
          stroke="blue"
          stroke-width="4"
        />
        <circle
          cx="100"
          cy="10"
          r="8"
          fill="none"
          stroke="blue"
          stroke-width="4"
        />
        <line
          x1="30"
          y1="10"
          x2="90"
          y2="10"
          style="stroke:blue;stroke-width:7"
        />
        <foreignObject
          x="30"
          y="20"
          width="180"
          height="80"
          requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"
        >
          <body xmlns="http://www.w3.org/1999/xhtml">
            <div class="text-block">
              <h3>{{ item.registered.split(",")[1] }}</h3>
              <p>{{ item.about.slice(0, 100) }}</p>
            </div>
          </body>
        </foreignObject>
      </g>

      <g
        v-else
        :transform="'translate(90, ' + (20 + 70 * index) + '), rotate(180)'"
      >
        <circle
          cx="10"
          cy="10"
          r="8"
          fill="blue"
          stroke="blue"
          stroke-width="4"
        />
        <circle
          cx="80"
          cy="10"
          r="8"
          fill="none"
          stroke="blue"
          stroke-width="4"
        />
        <line
          x1="20"
          y1="10"
          x2="70"
          y2="10"
          style="stroke:blue;stroke-width:7"
        />
        <foreignObject
          transform="translate(180, 20), rotate(180)"
          x="30"
          y="20"
          width="180"
          height="80"
          requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"
        >
          <body xmlns="http://www.w3.org/1999/xhtml">
            <div class="text-block">
              <h3>{{ item.registered.split(",")[1] }}</h3>
              <p>{{ item.about.slice(0, 100) }}</p>
            </div>
          </body>
        </foreignObject>
      </g>
    </g>
  </svg>
</template>

<script>
export default {
  created() {
    console.log(this.timeline); //undefined;
  },
  name: "Timeline",
  props: {
    filled: Boolean,
    timeline: Array
  },
  components: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  color: blue;
  margin-bottom: 0.2em;
  font-size: 10px;
}
p {
  margin: 0;
  font-size: 8px;
}
.text-block {
  max-width: 120px;
}
</style>
