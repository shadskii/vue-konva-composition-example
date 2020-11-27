<template>
  <v-layer>
    <v-circle :config="configCircle"></v-circle>
  </v-layer>
</template>

<script>
export default {
  inject: ['configKonva'],
  data() {
    return {};
  },
  computed: {
    configCircle() {
      return {
        x: this.configKonva.width / 2,
        y: 200,
        radius: 100,
        fill: 'blue',
        stroke: 'black',
        strokeWidth: 0
      };
    }
  }
};
</script>

<style></style>
