<script setup lang="ts">
import { defineProps } from "vue";

type Props = {
  bg?: string;
};

withDefaults(defineProps<Props>(), {
  bg: "bg-gray-100",
});
</script>

<template>
  <div :class="`${bg} p-6 rounded-lg shadow-md`">
    <slot></slot>
  </div>
</template>
