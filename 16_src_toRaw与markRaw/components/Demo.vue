<template>
  <h3>当前求和为：{{ sum }}</h3>
  <button @click="sum++">SUM的值修改</button>
  <hr />
  <h1>一个人的信息</h1>
  <h2>person:{{ person }}</h2>
  <h3>当前此人的名字为：{{ name }}</h3>
  <h3>当前此人的年龄为：{{ age }}</h3>
  <h3>当前此人的薪水为：{{ job.j1.salary }}</h3>
  <h3 v-show="person.car">此人的座驾信息为：{{ person.car }}</h3>
  <button @click="name += '~'">修改姓名</button>
  <button @click="age++">增长年龄</button>
  <button @click="job.j1.salary++">涨薪</button>
  <button @click="showPersonRaw">输出最原始的person</button>
  <button @click="addCar">给人添加一台车</button>
  <button @click="changeCarName" v-show="person.car">给车改名字</button>
  <button @click="person.car.price++" v-show="person.car">给车的价格++</button>
</template>

<script>
import { markRaw, reactive, ref, toRaw, toRefs } from "vue";
export default {
  name: "Demo",
  setup() {
    //数据
    let sum = ref(0);
    let person = reactive({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });
    let car = {
      name: "莱布尼斯",
      price: 40,
    };
    function addCar() {
      person.car = markRaw(car);
    }
    function showPersonRaw() {
      const p = toRaw(person);
      p.age = 20;
      console.log(p);
    }
    function changeCarName() {
      person.car.name = "奔驰";
    }

    return {
      sum,
      person,
      ...toRefs(person),
      showPersonRaw,
      addCar,
      changeCarName,
    };
  },
};
</script>

<style></style>
