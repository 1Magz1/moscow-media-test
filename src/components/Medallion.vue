<template>
    <div
        class="relative rounded-full bg-ring/40 ring-container shrink-0"
        :class="sizeClass"
    >
        <div
            class="absolute rounded-full overflow-hidden cursor-pointer group z-10"
            :class="innerInset"
        >
        <img
            :src="image"
            :alt="alt"
            class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
        />
        </div>

        <img
            src="../assets/images/decor-ring.png"
            alt="Декоративная рамка"
            class="absolute inset-0 w-full h-full object-contain pointer-events-none z-20 scale-95"
        />
    </div>
</template>

<script setup lang="ts">
const props = withDefaults(defineProps<{
    image: string;
    alt: string;
    sizeClass?: string;
    innerInset?: string;
}>(), {
    sizeClass: 'w-80 h-80',
    innerInset: 'inset-10',
});
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