<script setup>
const props = defineProps({
  title: String,
  icon: String,
  titlePosition: {
    type: String,
    default: 'left',
    validator(value) {
      return ['left', 'right'].includes(value)
    },
  },
})

const titlePosition = computed(() => {
  return props.titlePosition === 'right' ? 'self-end rotate-1' : '-rotate-3'
})

const iconPosition = computed(() => {
  return {
    'right-6 rotate-6': props.titlePosition === 'left',
    'left-6 -rotate-6': props.titlePosition === 'right',
  }
})
</script>

<template>
  <section
    class="max-w-screen-lg mx-auto px-4 md:px-8 lg:px-4 flex flex-col relative"
  >
    <Icon
      :name="icon"
      class="absolute text-gray-200 dark:text-slate-700 -top-12 transition"
      :class="iconPosition"
      size="124px"
    />
    <h2
      class="font-swanky text-slate-800 dark:text-slate-100 text-4xl mb-20 transition"
      :class="titlePosition"
    >
      {{ title }}
    </h2>
    <slot />
  </section>
</template>
