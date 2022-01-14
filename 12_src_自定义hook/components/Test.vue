<template>
  <h3>当前点的坐标为x：{{ point.x }},y:{{ point.y }}</h3>
</template>

<script>
import usePoint from "../hooks/usePoint";
export default {
  name: "Test",
  setup() {
    let point = usePoint();
    return {
      point,
    };
  },
};
</script>

<style></style>
