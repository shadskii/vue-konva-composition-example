<template>
  <div ref="stageParent" class="bg">
    <v-stage :config="configKonva" ref="stage">
      <v-layer>
        <v-circle :config="configCircle"></v-circle>
      </v-layer>
      <konva-layer />
    </v-stage>
  </div>
</template>
<script>
import KonvaLayer from './KonvaLayer.vue';

export default {
  name: 'KonvaStage',
  components: {
    KonvaLayer
  },
  provide() {
    return {
      configKonva: this.configKonva
    };
  },
  data() {
    return {
      configKonva: {
        width: 400,
        height: 400
      },
      configCircle: {
        x: 100,
        y: 100,
        radius: 70,
        fill: 'red',
        stroke: 'black',
        strokeWidth: 4
      }
    };
  },
  mounted() {
    window.addEventListener('resize', this.fitStageIntoParentContainer);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.fitStageIntoParentContainer);
  },
  methods: {
    fitStageIntoParentContainer() {
      const container = this.$refs.stageParent;
      const { width, height } = this.configKonva;
      const stage = this.$refs.stage.getNode();

      // now we need to fit stage into parent
      const containerWidth = container.offsetWidth;
      // to do this we need to scale the stage
      const scale = containerWidth / width;

      stage.width(width * scale);
      stage.height(height * scale);
      stage.scale({ x: scale, y: scale });
      stage.draw();
    }
  }
};
</script>

<style>
.bg {
  background-color: black;
}
</style>
