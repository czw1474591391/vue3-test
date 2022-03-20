<template>
  <div v-if="isShow">
    <h3>一个人的信息</h3>
    姓：<input type="text" v-model="person.firstName" />
    <br />
    名：<input type="text" v-model="person.lastName" />
    <br />
    姓名：<input type="text" v-model="person.fullName" />
  </div>
</template>

<script setup>
import { reactive, computed, defineProps } from 'vue';
defineProps({
  isShow: {
    type: Boolean,
    default: true
  }
});
const person = reactive({
  firstName: '',
  lastName: ''
});

// 计算属性简写、传入函数返回计算后的值（只能读取不能修改）
// person.fullName = computed(() => person.firstName + '-' + person.lastName);
// 计算属性完整写法、传入对象修改get set方法（可读可写）
person.fullName = computed({
  get() {
    return person.firstName + '-' + person.lastName;
  },
  set(value) {
    const nameArr = value.split('-');
    person.firstName = nameArr[0];
    person.lastName = nameArr[1];
  }
});
</script>

<style></style>
