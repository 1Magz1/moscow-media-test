<template>
    <div class="w-full flex flex-col items-center gap-4 mt-8 relative">
        <Swiper
        :modules="modules"
        :slides-per-view="1"
        :space-between="20"
        :pagination="{ clickable: true }"
        :navigation="{
            prevEl: '.custom-nav-prev',
            nextEl: '.custom-nav-next',
            disabledClass: 'swiper-button-disabled'
        }"
        class="w-full px-4"
        >
        <SwiperSlide v-for="item in items" :key="item.id">
            <div class="flex flex-col items-center gap-6 pb-12 mt-2">
            <Medallion
                :image="item.image"
                :alt="item.title"
                size-class="w-64 h-64"
                inner-inset="inset-[10%]"
            />
            <div class="text-center flex flex-col gap-3 px-2">
                <h2 class="text-2xl font-bold text-brown uppercase tracking-wide">
                {{ item.title }}
                </h2>
                <p class="text-text text-sm leading-relaxed">
                {{ item.description }}
                </p>
            </div>
            </div>
        </SwiperSlide>
        </Swiper>

        <button class="custom-nav-btn custom-nav-prev" aria-label="Назад">
        <img src="../assets/images/arrow.png" alt="" class="w-6 h-6" />
        </button>
        <button class="custom-nav-btn custom-nav-next" aria-label="Вперёд">
        <img src="../assets/images/arrow.png" alt="" class="w-6 h-6 rotate-180" />
        </button>
    </div>
</template>

<script setup lang="ts">
import type { TimelineCard } from '../data/timeline';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Navigation, Pagination } from 'swiper/modules';
import Medallion from './Medallion.vue';

import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

defineProps<{
    items: TimelineCard[];
}>();

const modules = [Navigation, Pagination];
</script>

<style scoped>
.custom-nav-btn {
    position: absolute;
    top: 40%;
    transform: translateY(-50%);
    z-index: 50;
    cursor: pointer;
    background-color: rgba(214, 185, 123, 0.7);
    border-radius: 50%;
    padding: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    border: none;
    transition: background-color 0.3s, opacity 0.3s;
}

.custom-nav-btn:hover {
    background-color: rgba(214, 185, 123, 1);
}

.custom-nav-prev { left: 0; }
.custom-nav-next { right: 0; }

.custom-nav-btn.swiper-button-disabled {
    opacity: 0.4;
    pointer-events: none;
}

:deep(.swiper-pagination-bullet) {
    background: var(--color-brown);
    opacity: 0.3;
}
:deep(.swiper-pagination-bullet-active) {
    opacity: 1;
    transform: scale(1.2);
}
</style>