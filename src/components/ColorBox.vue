<template>
  <div
    class="color-box"
    :style="{ backgroundColor: color }"
    @click="handleClick"
  >
  </div>
</template>

<script>
export default {
  props: ['color'],
  methods: {
    handleClick() {
      this.$emit('colorClick', this.color);
    },
  },
};
</script>

<style scoped>
.color-box {
  width: 100px;
  height: 100px;
  cursor: pointer;
  transition: transform 0.2s;
}

.color-box:hover {
  transform: scale(1.1);
}
</style>