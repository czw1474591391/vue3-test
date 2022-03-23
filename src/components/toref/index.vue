<template>
  <div v-if="isShow">
    <div>{{ name }}</div>
  <div>{{ age }}</div>
  <button>更改姓名</button>
  </div>
</template>

<script setup>
import { reactive, toRef, toRefs, defineProps } from 'vue';
defineProps({
  isShow: {
    type: Boolean,
    default: true
  }
});
const person1 = reactive({
  name: '张三',
  age: 15
});
const name = toRef(person1, 'name'); // 导出单个ref对象
const { age } = toRefs(person1); // 批量导出多个ref对象，可以解构
</script>

<style></style>
