<template>
  <div id="nav">
    <setup :data="123" @hello="helloClg" :isShow="false">
      <template v-slot:abc>
        <h3>具名插槽</h3>
      </template>
    </setup>
    <computed :isShow="false"></computed>
    <watch :isShow="false"></watch>
    <!-- <Teleport1></Teleport1> -->
    <Toref :isShow="false"></Toref>
    <shallowreactive :isShow="false"></shallowreactive>
    <toraw :isShow="true"></toraw>
  </div>
</template>
<script setup>
import setup from './components/setup-test';
import computed from './components/computed';
import watch from './components/watch';
// import Teleport1 from './components/teleport';
import Toref from './components/toref';
import shallowreactive from './components/shoallowReactive';
import toraw from './components/toRaw';

import { provide } from 'vue';
provide('info', helloClg);

function helloClg() {
  console.log('父组件的方法');
}
</script>
<style lang="scss"></style>
