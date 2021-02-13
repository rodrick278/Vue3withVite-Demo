<template>
  <Composition></Composition>
  <!-- Teleport:ModelButton -->
  <ModelButton></ModelButton>
</template>

<script>
import {} from "vue";

import Composition from "./Composition.vue";
import ModelButton from "./ModelButton.vue";

export default {
  name: "HelloWorld",
  components: {
    Composition,
    ModelButton
  },
};
</script>
