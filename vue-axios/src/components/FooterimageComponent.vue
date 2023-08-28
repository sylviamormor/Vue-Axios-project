<script setup>
import { defineProps } from 'vue';
defineProps(['images', 'cardtext'])


</script>

<template>
  <div class="footer">
    <img :src="images" alt="">
    <p>{{ cardtext }}</p>
  
  </div>
</template>

<style scoped>
.footer{
  display: flex;
}
</style>