<script setup lang="ts">
const isOpen = ref(false)
const { enable } = useConfig().value.search
const duration = 0.5

const commandCenterVariants = {
  pressed: { pathLength: 0.05 },
  checked: { pathLength: 0 },
  unchecked: { pathLength: 1 },
}
const route = useRoute()
watch(() => route.path, (value) => {
  isOpen.value = false
})
</script>

<template>
  <div class="flex place-items-center relative">
    <UiButton
      v-if="enable"
      class="absolute z-10 w-6 h-6 left-1 text-sm svg:!size-3"
      variant="ghost"
      size="icon"
    >
      <Motion
        as="svg"
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        :animate="isOpen ? 'checked' : 'unchecked'"
      >
        <Motion
          as="circle"
          cx="11"
          cy="11"
          r="8"
          :initial="{ pathLength: 1 }"
          :variants="commandCenterVariants"
          :transition="{ duration }"
        />
        <Motion
          as="path"
          d="m21 21-4.3-4.3"
          :initial="{ pathLength: 1 }"
          :variants="commandCenterVariants"
          :transition="{ duration }"
        />
      </Motion>
    </UiButton>
    <button
      class="pl-8 pr-16 h-8 relative flex place-items-center border border-border rounded-md hover:bg-accent cursor-pointer"
      placeholder="Search Documentation"
      @mousedown.prevent="isOpen = true"
    >
      <span class="text-sm">
        Search Documentation
      </span>
      <div class="px-2 py-[2px] bg-accent rounded-sm absolute right-1 text-sm">
        <span>
          /
        </span>
      </div>
    </button>
  </div>
  <LayoutHeaderDialog v-model:open="isOpen" />
</template>
