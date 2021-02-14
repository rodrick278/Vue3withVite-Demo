<template>
  <Composition></Composition>
  <!-- Teleport:ModelButton -->
  <ModalButton></ModalButton>
  <!-- Emits -->
  <Emits @click="myClick"></Emits>
  <!-- v-model -->
  <p>{{ strOne }}</p>
  <p>{{ strTwo }}</p>
  <Vmodel v-model:str1="strOne" v-model:str2="strTwo"></Vmodel>
</template>

<script>
import { ref } from "vue";

import Composition from "./Composition.vue";
import ModalButton from "./ModalButton.vue";
import Emits from "./Emits.vue";
import Vmodel from "./Vmodel.vue";

export default {
  name: "HelloWorld",
  components: {
    Composition,
    ModalButton,
    Emits,
    Vmodel,
  },
  setup() {
    // Vmodel 组件的初始值
    const strOne = ref("str1");
    const strTwo = ref("str2");
    const myClick = () => {
      console.log("外面的myClick");
    };
    return { myClick, strOne, strTwo };
  },
};
</script>
