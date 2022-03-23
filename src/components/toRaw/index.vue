<template>
  <div v-if="isShow">
    <h3>{{ person }}</h3>
    <h3>{{ 132 }}</h3>
    <h3>{{ person1 }}</h3>
    <h3>{{ person2 }}</h3>
    <button @click="person2.name += '-'">改变reactive中的数据</button>
  </div>
</template>

<script setup>
import { reactive, toRaw, defineProps, markRaw } from 'vue';
defineProps({
  isShow: {
    type: Boolean,
    default: true
  }
});
const obj = {
  name: '张三',
  job: {
    age: 1
  }
};
const obj2 = markRaw(obj); // markRaw是告诉vue这个对象不被proxy所代理
const person2 = reactive(obj2);

const person = reactive(obj);
const person1 = toRaw(person); // toRaw是将ref或reactive对象转换成普通对象

console.log(person1); // 结果都是普通对象
console.log(person2);
</script>

<style></style>
