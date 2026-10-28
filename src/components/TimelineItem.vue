<template>
  <div class="flex items-center gap-12 w-full max-w-5xl mx-auto py-12">
    <div
      class="relative w-80 h-80 rounded-full bg-ring/40 ring-container"
      :class="{ 'order-2': isReversed }"
    >
      <div class="absolute inset-10 rounded-full overflow-hidden cursor-pointer group z-10">
        <img
          :src="event.image"
          :alt="event.title"
          class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
        />
      </div>

      <img
        src="../assets/images/decor-ring.png"
        alt="Декоративная рамка"
        class="absolute inset-0 object-contain pointer-events-none z-20 scale-95"
      />
    </div>

    <!-- Текстовая часть -->
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

defineProps<{
  event: TimelineCard;
  isReversed?: boolean;
}>();
</script>

<style scoped>
.ring-container::after {
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 105%;
  height: 105%;
  border-radius: 50%;
  border: 1px solid var(--color-decor);
  pointer-events: none;
}
</style>