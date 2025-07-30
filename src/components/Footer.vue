<template>
    <footer class="bg-gray-900 text-white">
        <div class="py-10 flex items-center justify-center">
            <div class="container mx-auto px-4 sm:px-6 lg:px-30">
                <div class="text-center">
                    <p class="text-white text-[15px] pb-5">Find Us</p>
                    <h2 class="md:text-3xl text-[40px] font-bold mb-4 uppercase">At Your Doorstep</h2>
                    <div class=" flex justify-center items-center" style="margin-top: 20px;">
                        <div class="h-[3px] w-[150px] bg-[#96bd20] mx-auto"></div> 
                    </div>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 xl:grid-cols-4 gap-8 mt-10" style="margin: 16px 0; ">
                    <div v-for="(branch, index) in branches" :key="index" class="footer-widget">
                        <h4 class="text-[#e87000] font-semibold text-lg mb-3">
                            {{ branch.title }}
                        </h4>
                        <ul class="space-y-2 text-sm">
                            <li v-if="branch.address" class="flex items-start gap-2">
                                <i class="fa fa-map-marker-alt mt-1"></i>
                                <span>{{ branch.address }}</span>
                            </li>
                            <li v-if="branch.phone" class="flex items-start gap-2">
                                <i class="fa fa-phone mt-1"></i>
                                <span>{{ branch.phone }}</span>
                            </li>
                            <li v-if="branch.email" class="flex items-start gap-2">
                                <i class="fa fa-envelope mt-1"></i>
                                <span>{{ branch.email }}</span>
                            </li>
                        </ul>
                    </div>
                </div>

                <div class="mt-10 relative">
                    <div class="flex justify-end items-center gap-4 mb-4 text-lg">
                        <a href="https://www.facebook.com/EducationHubLtd/" target="_blank"><i
                                class="fab fa-facebook-f"></i></a>
                        <a href="https://www.instagram.com/educationhubltd/" target="_blank"><i
                                class="fab fa-instagram"></i></a>
                        <a href="https://www.linkedin.com/company/educationhubltd" target="_blank"><i
                                class="fab fa-linkedin-in"></i></a>
                        <a href="https://www.youtube.com/@EducationHubLtd" target="_blank"><i
                                class="fab fa-youtube"></i></a>
                        <a href="https://twitter.com/EducationHubLtd" target="_blank"><i class="fab fa-twitter"></i></a>
                    </div>

                    <img src="https://www.ehlweb.theskyroute.com/gerow/img/footer-below.png" alt=""
                        class="w-full h-auto" />
                </div>
            </div>
        </div>
        

        <div class="bg-black py-3 text-white text-sm flex items-center justify-center">
            <div class="container mx-auto px-4 sm:px-6 lg:px-30">
                <div class="flex flex-col md:flex-row justify-between items-center gap-3">
                <!-- Left: Copyright -->
                <div class="text-center md:text-left">
                    Copyright © 2023 Education Hub Ltd
                </div>

                <!-- Right: Links -->
                <div class="flex flex-wrap justify-center md:justify-end items-center gap-3">
                    <a href="#" class="hover:underline">
                    Be a Partner
                    </a>
                    <a href="#" class="hover:underline">
                    Privacy Policy
                    </a>
                    <a href="#" class="hover:underline">
                    Terms & Conditions
                    </a>
                    <span>|</span>
                    <span>
                    Developed with ❤️ By
                    <a href="#" target="_blank" class="underline">
                        Taskco Digital
                    </a>
                    </span>
                </div>
                </div>
            </div>
        </div>

    </footer>
</template>

<script setup>
const branches = [
  {
    title: "London Branch",
    address: "Mirror Works, 12 Marshgate Lane, London, E15, 2NH, United Kingdom.",
    phone: "+44(0)2032872554",
    email: "info@educationhub-bd.com",
  },
  {
    title: "Gulshan Branch",
    address: "Level 7, Manama MS Toren, Gulshan Badda Link Road. Dhaka 1212.",
    phone: "+8809666779911",
    email: "dhaka@educationhub-bd.com",
  },
  {
    title: "Dhanmondi Branch",
    address: "Level 5, Bikalpa Tower, Road 5/A, Dhanmondi, Dhaka 1209.",
    phone: "+8801844536601",
    email: "dhanmondi@educationhub-bd.com",
  },
  {
    title: "Chattogram Branch",
    address: "Rubiya Tower, Level 5, Road 03, Zakir Hossain Road, South Khulshi, Chattogram 4225.",
    phone: "+8801844536631",
    email: "chattogram@educationhub-bd.com",
  }
]
</script>

<style scoped>
.footer-widget i {
    color: #ffffffcc;
}
</style>
