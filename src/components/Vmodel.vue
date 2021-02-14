<template>
  <div>
    <p>str1:<input type="text" :value="str1" @input="str1use" /></p>
    <p>str2:<input type="text" :value="str2" @input="str2use" /></p>
  </div>
</template>

<script>
export default {
  name: "Vmodel",
  props: {
    str1: String,
    str2: String,
  },
  setup(props, ctx) {
    const str1use = (e) => {
      ctx.emit("update:str1", e.target.value);
    };
    const str2use = (e) => {
      ctx.emit("update:str2", e.target.value);
    };
    return { str1use, str2use };
  },
};
</script>

<style scoped>
</style>