<template>
  <div @click="$emit('click')">自定义事件</div>
</template>

<script>
export default {
  name: "Emits",
  emits: ["click"],
  setup() {
    return {};
  },
};
</script>

<style  scoped>
</style>