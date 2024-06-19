<script>
import ColorBox from './components/ColorBox.vue';

export default {
  components: {
    ColorBox,
  },
  data() {
    return {
      colors: ['red', 'green', 'blue', 'yellow', 'purple', 'orange'],
      targetColor: '',
      message: '',
    };
  },
  created() {
    this.setNewTargetColor();
  },
  methods: {
    setNewTargetColor() {
      this.targetColor = this.colors[Math.floor(Math.random() * this.colors.length)];
    },
    handleColorClick(color) {
      if (color === this.targetColor) {
        this.message = 'Correct!';
        this.setNewTargetColor();
      } else {
        this.message = 'Try again!';
      }
    },
  },
};
</script>

<template>
    <div class="app">
    <h1>Color Matching Game</h1>
    <h2>Match this color: <span :style="{ color: targetColor }">{{ targetColor }}</span></h2>
    <div class="color-boxes">
      <ColorBox
        v-for="color in colors"
        :key="color"
        :color="color"
        @colorClick="handleColorClick"
      />
    </div>
    <p>{{ message }}</p>
  </div>
</template>

<style scoped>
.app {
  text-align: center;
  font-family: Arial, sans-serif;
}

.color-boxes {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 10px;
  margin: 20px 0;
}
</style>
