<template>
  <li>
    <div
      class="flex justify-between items-center cursor-pointer font-medium"
      @click="isOpen = !isOpen"
    >
      {{ label }}
      <i :class="['fas', isOpen ? 'fa-chevron-up' : 'fa-chevron-down']"></i>
    </div>
    <transition name="fade">
      <ul v-if="isOpen" class="mt-2 pl-4 border-l border-gray-300 space-y-2">
        <li v-for="item in items" :key="item.href">
          <a :href="item.href" class="block text-gray-700 hover:text-blue-600">
            {{ item.name }}
          </a>
        </li>
      </ul>
    </transition>
  </li>
</template>

<script setup>
import { ref } from 'vue'

defineProps({
  label: String,
  items: Array
})

const isOpen = ref(false)
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-5px);
}
</style>
