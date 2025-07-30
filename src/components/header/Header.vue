<template>
  <header class="bg-white shadow-md">
    <!-- Top Bar -->
    <div class="bg-[#051433] py-4 flex items-center justify-center">
      <div class="container mx-auto px-4 sm:px-6 lg:px-30 flex flex-col lg:flex-row justify-between items-center text-sm text-[#e6eeff]">
        <div class="flex gap-6 mb-2 lg:mb-0">
          <a href="tel:+44(0)2032872554" class="flex items-center gap-2">
            <i class="fa fa-phone"></i> +44(0)2032872554
          </a>
          <a href="mailto:info@education-hub.co.uk" class="flex items-center gap-2">
            <i class="far fa-envelope"></i> info@education-hub.co.uk
          </a>
        </div>
        <div class="flex items-center gap-4">
          <a href="https://www.facebook.com/EducationHubLtd/" target="_blank"><i class="fab fa-facebook-f"></i></a>
          <a href="https://www.instagram.com/educationhubltd/" target="_blank"><i class="fab fa-instagram"></i></a>
          <a href="https://www.linkedin.com/company/educationhubltd" target="_blank"><i class="fab fa-linkedin-in"></i></a>
          <a href="https://www.youtube.com/@EducationHubLtd" target="_blank"><i class="fab fa-youtube"></i></a>
          <a href="https://twitter.com/EducationHubLtd" target="_blank"><i class="fab fa-twitter"></i></a>
          <a
            href="#"
            class="bg-[#96bd20] text-black font-semibold px-4 py-1.5 rounded-md hover:bg-[#e87000]"
          >
            Apply Online
          </a>
        </div>
      </div>
    </div>

    <!-- Navbar -->
     <div class="flex items-center justify-center h-24 sticky top-0 bg-white shadow-md z-50">
         <nav class="container mx-auto px-4 sm:px-6 lg:px-30 flex items-center justify-between py-4 relative">
           <!-- Logo -->
           <a href="/" class="h-8 w-3/12">
             <img
               src="https://www.ehlweb.theskyroute.com/assets/front/img/634544bbb5db0.png"
               alt="Logo"
               class="h-full w-auto"
             />
           </a>
     
           <!-- Desktop Menu -->
            <div class="hidden lg:flex w-7/12 justify-end">
             
                <ul class="gap-[30px] flex items-center font-medium text-gray-800">
                  <DropdownMenu label="Study Abroad" :items="studyAbroadLinks" />
                  <DropdownMenu label="Services" :items="servicesLinks" />
                  <DropdownMenu label="Resources" :items="resourcesLinks" />
                  <li><a href="/future-career">Future Career</a></li>
                  <li><a href="/about-us">About Us</a></li>
                  <li><a href="/contact">Contact</a></li>
                </ul>
            </div>
           <div class="hidden lg:flex items-center justify-center w-2/12 ">
               <a
                   href="#"
                   class="btn ml-6 bg-[#e87000] text-white px-6 py-4 rounded-full hover:bg-[#96bd20]"
               >
                   Find Course
               </a>
           </div>

           <!-- Mobile Toggle -->
           <button class="lg:hidden text-xl" @click="toggleMobileMenu">
             <i class="fas fa-bars"></i>
           </button>
     
           <!-- Mobile Menu -->
           <MobileMenu v-if="isMobileOpen" @close="isMobileOpen = false" />
         </nav>
     </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'
import DropdownMenu from './DropdownMenu.vue'
import MobileMenu from './MobileMenu.vue'

const isMobileOpen = ref(false)

function toggleMobileMenu() {
  isMobileOpen.value = !isMobileOpen.value
}

const studyAbroadLinks = [
  { name: 'Study in UK', href: '/study-abroad/uk' },
  { name: 'Study in USA', href: '/study-abroad/usa' },
  { name: 'Study in Canada', href: '/study-abroad/canada' },
  { name: 'Study in Australia', href: '/study-abroad/australia' },
  { name: 'Study in Malaysia', href: '/study-abroad/malaysia' },
  { name: 'Study in Denmark', href: '/study-abroad/denmark' },
  { name: 'Study in Netherlands', href: '/study-abroad/netherlands' },
  { name: 'Study in France', href: '/study-abroad/france' },
  { name: 'Study in Dubai', href: '/study-abroad/dubai' },
]

const servicesLinks = [
  { name: 'Admission', href: '/service/Admission' },
  { name: 'Scholarships', href: '/service/Scholarships' },
  { name: 'Visa Guidance', href: '/service/Visa-Guidance' },
  { name: 'Departure Guidance', href: '/service/Departure-Guidance' },
  { name: 'IELTS Registration & Mock Test', href: '/service/IELTS-Registration-&-Mock-Test' },
  { name: 'Career Counseling', href: '/service/career-counseling' },
]

const resourcesLinks = [
  { name: 'Events', href: '/events' },
  { name: 'Blogs', href: '/blogs' },
  { name: 'Top Universities', href: '/top-universities' },
  { name: 'Popular Subjects', href: '/popular-subjects' },
  { name: 'Student Essentials', href: '/student-essentials' },
]
</script>

