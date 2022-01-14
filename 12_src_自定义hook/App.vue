<template>
  <button @click="isShow = !isShow">点击展示和关闭Demo 组件</button>
  <Demo v-if="isShow"></Demo>
  <Test></Test>
</template>

<script>
import { ref } from "@vue/reactivity";
import Demo from "./components/Demo";
import Test from "./components/Test";
export default {
  name: "App",
  components: { Demo, Test },
  setup() {
    let isShow = ref(true);
    return { isShow };
  },
};
</script>

<style></style>
