<template>
  <div
    class="fixed inset-0 bg-white z-50 p-6 overflow-y-auto md:hidden"
  >
    <div class="flex justify-between items-center mb-6">
      <a href="/" class="text-xl font-bold">EHL</a>
      <button @click="$emit('close')">
        <i class="fas fa-times text-xl"></i>
      </button>
    </div>

    <ul class="space-y-4">
      <MobileNavItem label="Study Abroad" :items="studyAbroadLinks" />
      <MobileNavItem label="Services" :items="servicesLinks" />
      <MobileNavItem label="Resources" :items="resourcesLinks" />
      <li><a href="#" class="block">Future Career</a></li>
      <li><a href="#" class="block">About Us</a></li>
      <li><a href="#" class="block">Contact</a></li>
      <li>
        <a
          href="#"
          class="block bg-[#e87000] hover:bg-[#96bd20] px-4 py-2 rounded font-bold text-center"
        >
          Apply Online
        </a>
      </li>
    </ul>
  </div>
</template>

<script setup>
import MobileNavItem from './MobileNavItem.vue'

const studyAbroadLinks = [
  { name: 'Study in UK', href: '#' },
  { name: 'Study in USA', href: '#' },
  { name: 'Study in Canada', href: '#' },
  { name: 'Study in Australia', href: '#' },
  { name: 'Study in Malaysia', href: '#' },
  { name: 'Study in Denmark', href: '#' },
  { name: 'Study in Netherlands', href: '#' },
  { name: 'Study in France', href: '#' },
  { name: 'Study in Dubai', href: '#' },
]

const servicesLinks = [
  { name: 'Admission', href: '#' },
  { name: 'Scholarships', href: '#' },
  { name: 'Visa Guidance', href: '#' },
  { name: 'Departure Guidance', href: '#' },
  { name: 'IELTS Registration & Mock Test', href: '#' },
  { name: 'Career Counseling', href: '#' },
]

const resourcesLinks = [
  { name: 'Events', href: '#' },
  { name: 'Blogs', href: '#' },
  { name: 'Top Universities', href: '#' },
  { name: 'Popular Subjects', href: '#' },
  { name: 'Student Essentials', href: '#' },
]
</script>

<style scoped>
@media (min-width: 768px) {
  .md\:hidden {
    display: none;
  }
}
</style>
