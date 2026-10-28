<script setup lang="ts">
import TimelineItem from './components/TimelineItem.vue';
import { timelineData } from './data/timeline';
</script>

<template>
    <div class="text-center my-16">
      <h1 class="text-5xl font-bold text-white uppercase tracking-wider drop-shadow-md">
        История московского<br/>ипподрома
      </h1>
    </div>

    <div class="hidden md:flex flex-col gap-12">
      <TimelineItem
        v-for="(item, index) in timelineData"
        :key="item.id"
        :event="item"
        :is-reversed="index % 2 !== 0"
      />
    </div>
</template>
