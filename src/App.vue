<script setup lang="ts">
import TimelineItem from './components/TimelineItem.vue';
import HorseTicker from './components/HorseTicker.vue';
import { timelineData } from './data/timeline';
</script>

<template>
    <HorseTicker/>
    <div class="text-center my-18">
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
