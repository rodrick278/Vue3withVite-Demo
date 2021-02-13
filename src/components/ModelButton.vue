<template>
  <div>
    <button @click="modelflag = true">弹出模态窗口</button>

    <!-- to:选择器 -->
    <teleport to="body">
      <div v-if="modelflag" class="model">
        <div>这里是一个弹窗</div>
        <button @click="close">click close</button>
      </div>
    </teleport>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "ModelButton",
  setup() {
    let modelflag = ref(true);

    const close = () => {
      modelflag.value = false;
    };

    return { modelflag, close };
  },
};
</script>

<style scoped>
.model {
  position: fixed;
  width: 100px;
  height: 80px;
  background-color: #eee;
  left: 20%;
  top: 20%;
  transform: translate(-50%, -50%);
}
</style>