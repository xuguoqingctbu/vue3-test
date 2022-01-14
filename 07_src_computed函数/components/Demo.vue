<template>
  姓：<input
    type="text"
    name="firstName"
    v-model="person.firstName"
    placeholder="请输入姓氏"
  /><br />
  名：<input
    type="text"
    name="secondName"
    v-model="person.secondName"
    placeholder="请输入你的名"
  /><br />
  全名：<input type="text" v-model="person.fullName" /><br />
</template>

<script>
import { computed, reactive } from "@vue/reactivity";
export default {
  name: "Demo",
  setup() {
    let person = reactive({
      firstName: "张",
      secondName: "三",
    });
    //计算属性——简写（没有考虑计算属性被修改的情况）
    // person.fullName = computed(() => {
    //   return person.firstName + "-" + person.secondName;
    // });
    person.fullName = computed({
      get() {
        return person.firstName + "-" + person.secondName;
      },
      set(value) {
        const nameArr = value.split("-");
        person.firstName = nameArr[0];
        person.secondName = nameArr[1];
      },
    });
    return {
      person,
    };
  },
  //#region
  // computed: {
  //   //vue2 简写形式
  //   // fullName() {
  //   //   console.log(this);
  //   //   return this.person.firstName + "-" + this.person.secondName;
  //   // },
  //   fullName: {
  //     get() {
  //       return this.person.firstName + "-" + this.person.secondName;
  //     },
  //     set(value) {
  //       const nameArr = value.split("-");
  //       this.person.firstName = nameArr[0];
  //       this.person.secondName = nameArr[1];
  //     },
  //   },
  //},
  //#endregion
};
</script>

<style></style>
