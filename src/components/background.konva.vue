<template>
  <v-layer>
    <v-rect :config="config" />
  </v-layer>
</template>

<script>
export default {
  inject: ['configKonva'],
  computed: {
    config() {
      const { height, width } = this.configKonva;
      return {
        width,
        height,
        fill: '#121212'
      };
    }
  }
};
</script>

<style></style>
