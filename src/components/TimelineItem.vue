<template>
  <div class="flex items-center gap-12 w-full max-w-5xl mx-auto py-12">
        <div :class="{ 'order-2': isReversed }">
          <Medallion
            :image="event.image"
            :alt="event.title"
            @click="openLightbox"
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

        <Lightbox
          :is-open="isLightboxOpen"
          :src="event.image"
          :alt="event.title"
          @close="isLightboxOpen = false"
        />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import type { TimelineCard } from '../data/timeline';

import Medallion from './Medallion.vue';
import Lightbox from './Lightbox.vue';

defineProps<{
  event: TimelineCard;
  isReversed?: boolean;
}>();

const isLightboxOpen = ref(false);

const openLightbox = () => {
  isLightboxOpen.value = true;
};
</script>