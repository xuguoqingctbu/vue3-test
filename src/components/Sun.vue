<template>
  <div class="sun">我是孙组件</div>
</template>

<script>
import { inject, toRefs } from "vue";
export default {
  name: "Sun",
  setup() {
    let car = inject("car");
    return {
      ...toRefs(car),
    };
  },
};
</script>

<style scoped>
.sun {
  background-color: aqua;
  padding: 50px 0px;
}
</style>
