<script setup lang="tsx">
import { motion } from 'motion-v'
import { slideUp } from '@/lib/motion'

const links = [
  { text: 'Documentation', href: '#' },
  { text: 'Examples', href: '#' },
  { text: 'Showcase', href: '#' },
  { text: 'GitHub', href: '#' },
]

const features = [
  {
    icon: <Icon name="lucide:wand" />,
    title: 'Declarative Animations',
    description: 'Simple, declarative syntax for complex animations. Define animations with Vue templates, no imperative code needed.',
  },
  {
    icon: <Icon name="lucide:layout-grid" />,
    title: 'Layout Animations',
    description: 'Powerful FLIP animations for smooth layout transitions and shared element animations.',
  },
  {
    icon: <Icon name="lucide:hand" />,
    title: 'Gesture Controls',
    description: 'Rich gesture system for drag, pan, hover and press interactions with spring physics.',
  },
  {
    icon: <Icon name="lucide:box" />,
    title: 'Motion Values',
    description: 'Dynamic animation values that can be transformed, combined and spring-animated.',
  },
]

const floatingItems = [
  {
    class: 'w-8 h-8 rounded bg-green-500/20',
    style: { top: '15%', left: '10%', animationDelay: '0s' },
  },
  {
    class: 'w-12 h-12 rounded-full bg-blue-500/20',
    style: { top: '25%', right: '15%', animationDelay: '0.5s' },
  },
  {
    class: 'w-6 h-6 rounded-full bg-yellow-500/20',
    style: { bottom: '20%', left: '20%', animationDelay: '1s' },
  },
  {
    class: 'w-10 h-10 rounded bg-purple-500/20',
    style: { bottom: '30%', right: '25%', animationDelay: '1.5s' },
  },
]
</script>

<template>
  <div class="min-h-screen bg-background">
    <!-- Hero Section -->
    <div class="relative pt-28 pb-28 -mt-10 sm:pt-40 sm:pb-24">
      <!-- Main Content -->
      <motion.div
        initial="hidden"
        in-view="visible"
        :transition="{
          staggerChildren: 0.2,
        }"
        :in-view-options="{ once: true }"
        class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8"
      >
        <div class="text-center flex flex-col items-center">
          <div class="flex text-sm place-items-center pr-2 cursor-pointer hover:bg-accent w-fit mb-5 gap-3 border p-1 rounded-full border-border">
            <div class="newtag text-background font-bold flex place-items-center px-3 py-[2px] bg-primary rounded-full">
              New
            </div>
            V0.8.1 is out Now 🎉
            <Icon
              name="lucide:chevron-right"
              class="size-4 text-foreground"
            />
          </div>
          <motion.h1
            v-bind="slideUp"
            class="text-5xl  md:text-7xl font-bold text-foreground mb-2 "
          >
            Motion for
            <span class="text-green-500">Vue.</span>
          </motion.h1>
          <motion.p
            v-bind="slideUp"
            class="max-w-2xl mx-auto text-lg text-muted-foreground mb-7 "
          >
            Build beautiful motion-driven interfaces with Vue.js based on <a
              href="https://www.framer.com/motion/"
              target="_blank"
              class="text-primary hover:underline"
            >motion</a>.
            Simple, powerful, and performant animations for modern web applications.
          </motion.p>
          <motion.div
            v-bind="slideUp"
            class="flex justify-center space-x-4 "
          >
            <UiButton
              class="rounded-md text-background font-bold"
              as="a"
              href="/getting-started"
            >
              Get Started
            </UiButton>
            <div class="flex rounded-md place-items-center gap-3 border border-border p-1 px-3 pr-1">
              <Icon
                name="lucide:terminal"
                class="size-5 text-muted-foreground"
              />
              <span class="font-mono">
                npm i motion-v
              </span>
              <UiButton
                size="icon"
                variant="outline"
                class="flex ml-10 size-6"
              >
                <Icon
                  name="lucide:copy"
                  class="size-3 text-muted-foreground cursor-pointer"
                />
              </UiButton>
            </div>
          </motion.div>
        </div>
      </motion.div>
    </div>

    <!-- Features Grid -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20">
      <motion.div
        class="grid md:grid-cols-4 gap-8"
        initial="hidden"
        in-view="visible"
        :transition="{
          delayChildren: 0.2,
          staggerChildren: 0.1,
        }"
      >
        <motion.div
          v-for="feature in features"
          :key="feature.title"
          v-bind="slideUp"
          class="p-6 rounded-xl hover:bg-primary/5 transition-colors"
        >
          <div class="w-12 h-12 rounded-lg bg-primary/10 flex items-center justify-center mb-4">
            <component
              :is="feature.icon"
              class="w-6 h-6 text-primary"
            />
          </div>
          <h3 class="text-xl font-semibold mb-2">
            {{ feature.title }}
          </h3>
          <p class="text-muted-foreground">
            {{ feature.description }}
          </p>
        </motion.div>
      </motion.div>
    </div>
  </div>
</template>
