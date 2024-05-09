<script setup lang="ts">
import { defineComponent } from 'vue'

const props = defineProps({
  num: {
  },
  pattern: {
    default: "Anti-pattern",
  },
})
</script>

<template>
  <div class="absolute top-5px left-5px text-left">
    <h2>{{ props.pattern }} #{{ props.num }}</h2>
  </div>
</template>