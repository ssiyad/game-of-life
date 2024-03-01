<template>
  <div
    class="absolute inset-8 flex size-max items-center gap-1 rounded bg-blue-100 p-4 shadow dark:bg-indigo-900 dark:text-white"
  >
    <a class="flex items-center gap-1" href="/">
      <Icon icon="lucide:home" />
      <span>Home</span>
    </a>
    <Icon icon="lucide:dot" />
    <a
      class="flex items-center gap-1"
      href="https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life"
      target="_blank"
    >
      <Icon icon="lucide:info" />
      <span>Info</span>
    </a>
    <Icon icon="lucide:dot" />
    <div
      class="flex cursor-pointer items-center gap-1"
      @click="() => $emit('update:isPaused', !isPaused)"
    >
      <Icon icon="lucide:play" v-if="isPaused" />
      <Icon icon="lucide:pause" v-else />
      <span>
        {{ isPaused ? 'Resume' : 'Pause' }}
      </span>
    </div>
    <Icon icon="lucide:dot" />
    <div
      class="flex cursor-pointer items-center gap-1"
      @click="() => census.forEach((_, i) => (census[i] = false))"
    >
      <Icon icon="lucide:refresh-ccw" />
      <span>Reset</span>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Icon } from '@iconify/vue';

defineProps({
  isPaused: {
    type: Boolean,
    required: true,
  },
  census: {
    type: Array,
    required: true,
  },
});

defineEmits<{
  (event: 'update:isPaused', value: boolean): void;
}>();
</script>
