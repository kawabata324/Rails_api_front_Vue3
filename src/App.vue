import { defineComponent } from 'vue';
<template>
  <div class="app">
    <div class="">
      <router-link to= "/about">about</router-link>
      <router-link to= "/">home</router-link>
    </div>
    <router-view></router-view>
  </div>
</template>

<script lang = "ts">
import {defineComponent} from 'vue'

export default defineComponent({

});
</script>

<style></style>
