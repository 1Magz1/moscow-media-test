<script setup lang="ts">
import { computed } from 'vue';
import { useWindowScroll, useWindowSize } from '@vueuse/core';

const { y } = useWindowScroll();
const { width } = useWindowSize();

const speed = 1.2;

const offsetX = computed(() => {
	const startOffset = -width.value * 1.5;
	return startOffset + y.value * speed;
});
</script>

<template>
	<div class="fixed top-0 left-0 w-full z-50 overflow-hidden bg-bg py-4">
		<div
			class="flex w-max will-change-transform"
			:style="{ transform: `translateX(${offsetX}px)` }"
		>
			<img
				v-for="i in 4"
				:key="i"
				src="../assets/images/horses-ticker.png"
				alt="Бегущие лошади"
				class="h-10 w-auto object-contain mx-4"
			/>
		</div>
	</div>
</template>
