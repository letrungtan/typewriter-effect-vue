<script setup lang="ts">
import { onMounted, useTemplateRef, watch, type Ref } from 'vue';
import { tTypewriter } from '../../t-typewriter';

// Define the props with TypeScript interfaces
interface Props {
  id?: string;
  active?: boolean | null;
  speed?: number;
  delay?: number;
  isHideCursor?: boolean;
  hideCursorOnDone?: boolean;
}

const props = withDefaults(defineProps<Props>(), {
  id: '',
  active: null,
  speed: 50,
  delay: 0,
  isHideCursor: false,
  hideCursorOnDone: false,
});

const emit = defineEmits<{
  (event: 'done', id: string): void;
}>();

const contentRef: Ref<HTMLElement | null> = useTemplateRef('content')

// Function to start the typewriter effect
const start = async (): Promise<void> => {
  await new Promise((resolve) => setTimeout(resolve, 1));
  if (contentRef.value) {
    await tTypewriter(contentRef.value, {
      speed: props.speed,
      isHideCursor: props.isHideCursor,
      hideCursorOnDone: props.hideCursorOnDone
    });
  }

  emit('done', props.id);
};

// Watch for changes in the `active` prop
watch(
  () => props.active,
  (to) => {
    if (to) {
      start();
    }
  }
);

// Initialize on mount
onMounted(() => {
  if (props.active || props.active === null) {
    start();
  }
});
</script>

<template>
  <div ref="content" class="t-typewriter">
      <slot />
  </div>
</template>