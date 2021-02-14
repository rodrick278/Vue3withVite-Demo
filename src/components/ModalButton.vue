<template>
  <div>
    <button @click="modalflag = true">弹出模态窗口</button>

    <!-- to:选择器 -->
    <teleport to="body">
      <div v-if="modalflag" class="model">
        <div>
          这里是一个弹窗
          <button @click="close">click close</button>
        </div>
      </div>
    </teleport>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "ModalButton",
  setup() {
    let modalflag = ref(false);

    const close = () => {
      modalflag.value = false;
    };

    return { modalflag, close };
  },
};
</script>

<style scoped>
.model {
	position: fixed;
	left: 0;
	right: 0;
	top: 0;
	bottom: 0;
	background-color: rgba(126, 126, 126, .5);
}

.model div {
	position: fixed;
	left: 50%;
	top: 50%;
	width: 200px;
	height: 200px;
	background-color: #eee;
	line-height: 200px;
	transform: translate(-50%, -50%);
}

</style>