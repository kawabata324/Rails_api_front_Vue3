<template>
  <div>aa</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Client from "../api/client";
import { onMounted } from '@vue/runtime-core';

export default defineComponent({
  setup() {
    onMounted(()=>{
      Client.get("/api/memos").then((res) => {
        console.log(res);
      });
    })
    return {
    };
  },
});
</script>

<style></style>
