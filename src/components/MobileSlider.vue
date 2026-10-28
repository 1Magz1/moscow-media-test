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
            <div class="flex flex-col items-center gap-6 pb-12">
            <div class="relative w-64 h-64 rounded-full bg-ring/40 ring-container mt-2">
                <div class="absolute inset-[10%] rounded-full overflow-hidden cursor-pointer group z-10">
                <img
                    :src="item.image"
                    :alt="item.title"
                    class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
                />
                </div>
                <img
                    src="../assets/images/decor-ring.png"
                    alt="Декоративная рамка"
                    class="absolute inset-0 w-full h-full object-contain pointer-events-none z-20 scale-95"
                />
            </div>
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

        <button
            class="custom-nav-btn custom-nav-prev"
            @click="slidePrev"
            aria-label="Назад"
        >
        <img src="../assets/images/arrow.png" alt="" class="w-6 h-6" />
        </button>

        <button
            class="custom-nav-btn custom-nav-next"
            @click="slideNext"
            aria-label="Вперёд"
        >
        <img src="../assets/images/arrow.png" alt="" class="w-6 h-6  rotate-180" />
        </button>
    </div>
</template>

<script setup lang="ts">
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

import { ref } from 'vue';
import type { TimelineCard } from '../data/timeline';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Navigation, Pagination } from 'swiper/modules';
import type { Swiper as SwiperClass } from 'swiper';

defineProps<{
    items: TimelineCard[];
}>();

const modules = [Navigation, Pagination];

const swiperRef = ref<SwiperClass | null>(null);

const slidePrev = () => {
    swiperRef.value?.slidePrev();
};

const slideNext = () => {
    swiperRef.value?.slideNext();
};
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

.custom-nav-btn {
    position: absolute;
    top: 40%; /* примерно уровень медальона */
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

.custom-nav-prev {
    left: 0;
}

.custom-nav-next {
    right: 0;
}

.custom-nav-btn.swiper-button-disabled {
    opacity: 0.4;
    cursor: default;
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