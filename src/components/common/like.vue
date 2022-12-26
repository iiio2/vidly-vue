<template>
  <i :class="getClass" @click="onLike"></i>
</template>

<script setup lang="ts">
import { computed } from "vue";
const props = defineProps(["liked", "onLike"]);
const getClass = computed(() => {
  return props.liked ? "bi bi-balloon-heart-fill" : "bi bi-balloon-heart";
});
</script>
