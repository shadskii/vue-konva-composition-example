<template>
  <v-layer>
    <v-line v-for="(line, index) in gridLines" :config="line" :key="index" />
    <v-circle
      v-for="(circle, circleIndex) in circles"
      :config="circle"
      :key="`${circleIndex}-circle`"
    ></v-circle>
  </v-layer>
</template>

<script>
export default {
  inject: ['configKonva'],
  data() {
    return {};
  },
  computed: {
    gridLines() {
      const num = 10;
      const { width, height } = this.configKonva;
      const horizontal = Array(num)
        .fill(0)
        .map((_, index) => {
          return {
            x: 0,
            y: index * (height / num),
            stroke: 'black',
            points: [0, 0, width, 0],
            strokeWidth: 1
          };
        });
      const vertical = Array(num)
        .fill(0)
        .map((_, index) => {
          return {
            x: (index + 1) * (height / num),
            y: 0,
            stroke: 'black',
            points: [0, 0, 0, height],
            strokeWidth: 1
          };
        });

      return horizontal.concat(vertical);
    },
    circles() {
      return Array(5)
        .fill(0)
        .map((_, index) => {
          return {
            x: this.configKonva.width / 2,
            y: this.configKonva.height / 2,
            radius: (index * (this.configKonva.width / 2)) / 4,
            stroke: 'black',
            strokeWidth: 5
          };
        });
    },
    configCircle() {
      return {
        x: this.configKonva.width / 2,
        y: this.configKonva.height / 2,
        radius: 100,
        stroke: 'black',
        strokeWidth: 1
      };
    }
  }
};
</script>

<style></style>
