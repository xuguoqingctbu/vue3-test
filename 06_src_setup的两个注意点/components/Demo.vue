<template>
  <h1>一个人的信息</h1>
  <h2>姓名：{{ person.name }}</h2>
  <h2>年龄：{{ person.age }}</h2>
  <button @click="test">触发点击Demo组件的hello事件</button>
  <slot>我是一些默认值，当使用者没有传递具体结构时，我会出现</slot>
  <slot name="qwd">我是一些默认值，当使用者没有传递具体结构时，我会出现</slot>
  <slot name="sad">我是一些默认值，当使用者没有传递具体结构时，我会出现</slot>
  <slot name="list">我是一些默认值，当使用者没有传递具体结构时，我会出现</slot>
</template>

<script>
import { reactive } from "@vue/reactivity";
export default {
  name: "Demo",
  props: ["msg"],
  emits: ["hello", "school"],
  setup(props, context) {
    // console.log("---setup---", props);
    console.log("---setup---", context);
    // console.log("---setup---", context.attrs); //相当与Vue2中的$attrs
    // console.log("---setup---", context.emit); //触发自定义事件的。
    console.log("---setup---", context.slots); //插槽
    let person = reactive({
      name: "张三",
      age: 18,
    });
    function test() {
      console.log();
      context.emit("hello", person.name);
    }
    return {
      person,
      test,
    };
  },
};
</script>

<style></style>
