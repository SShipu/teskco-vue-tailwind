<template>
  <li class="relative group">
    <a href="#" class="cursor-pointer flex items-center gap-1 font-medium text-black hover:text-[#96bd20]">
      {{ label }}
      <i class="fas fa-angle-down text-sm"></i>
    </a>
    <ul
      class="absolute z-10 bg-white shadow-lg rounded py-2 mt-2 min-w-[180px] hidden group-hover:block"
    >
      <li v-for="item in items" :key="item.name">
        <a
          :href="item.href"
          class="block px-4 py-2 text-gray-700 hover:bg-gray-100 whitespace-nowrap"
        >
          {{ item.name }}
        </a>
      </li>
    </ul>
  </li>
</template>

<script setup>
defineProps({
  label: String,
  items: Array,
})
</script>
