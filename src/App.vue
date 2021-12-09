import { defineComponent } from 'vue';
<template>
  <div class="app">
    <div class="flex gap-6">
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
