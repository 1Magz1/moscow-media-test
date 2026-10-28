<template>
	<Teleport to="body">
		<Transition name="fade">
			<div
				v-if="isOpen"
				class="fixed inset-0 z-100 flex items-center justify-center bg-black/80 backdrop-blur-sm p-4"
				@click.self="close"
			>
				<button
					@click="close"
					class="absolute top-6 right-6 text-white hover:text-hippo-ring transition-colors z-10 cursor-pointer"
					aria-label="Закрыть"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="h-10 w-10"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M6 18L18 6M6 6l12 12"
						/>
					</svg>
				</button>

				<Transition name="zoom" appear>
					<img
						v-if="isOpen"
						:src="src"
						:alt="alt"
						class="max-w-full max-h-[90vh] object-contain rounded-lg shadow-2xl"
						@click.stop
					/>
				</Transition>
			</div>
		</Transition>
	</Teleport>
</template>

<script setup lang="ts">
defineProps<{
	isOpen: boolean;
	src: string;
	alt: string;
}>();

const emit = defineEmits<{
	(e: 'close'): void;
}>();

const close = () => {
	emit('close');
};
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
	transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
	opacity: 0;
}

.zoom-enter-active,
.zoom-leave-active {
	transition:
		transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275),
		opacity 0.4s ease;
}

.zoom-enter-from,
.zoom-leave-to {
	transform: scale(0.8);
	opacity: 0;
}
</style>
