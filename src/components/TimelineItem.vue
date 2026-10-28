<template>
  <div class="flex items-center gap-12 w-full max-w-5xl mx-auto py-12">
      <div :class="{ 'order-2': isReversed }">
        <Medallion
          :image="event.image"
          :alt="event.title"
        />
      </div>

      <div class="flex flex-col gap-4 flex-1" :class="{ 'order-1 text-right': isReversed }">
        <h2 class="text-3xl font-bold text-brown uppercase tracking-wide">
          {{ event.title }}
        </h2>
        <p class="text-text leading-relaxed text-lg">
          {{ event.description }}
        </p>
      </div>
  </div>
</template>

<script setup lang="ts">
import type { TimelineCard } from '../data/timeline';
import Medallion from './Medallion.vue';

defineProps<{
  event: TimelineCard;
  isReversed?: boolean;
}>();
</script>