<template>
  <div id="nav">
    <setup :data="123" @hello="helloClg" :isShow="false">
      <template v-slot:abc>
        <h3>具名插槽</h3>
      </template>
    </setup>
    <computed :isShow="false"></computed>
    <watch :isShow="true"></watch>
  </div>
</template>
<script setup>
import setup from './components/setup-test';
import computed from './components/computed';
import watch from './components/watch';

function helloClg() {
  console.log('父组件的方法');
}
</script>
<style lang="scss"></style>
