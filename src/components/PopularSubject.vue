<template>
    <section class="py-12 popular-subject flex items-center justify-center">
        <div class="container mx-auto px-4 sm:px-6 lg:px-30">
            <div class="text-center">
                <h2 class="text-3xl font-semibold text-[#e87000] uppercase">Explore Popular Subjects</h2>
                <p class="text-[#6c757d] text-lg mt-2">Discover the top subjects chosen by students worldwide.</p>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 pt-6">
                <template v-if="!loading">
                    <div v-for="subject in subjects" :key="subject.id" class="bg-white  flex flex-col">
                        <a :href="subject.detailUrl"
                            class="relative block pb-3 rounded-bl-md rounded-br-md rounded-tl-2xl rounded-tr-2xl overflow-hidden">
                            <img :src="subject.image" :alt="subject.name" class="w-full h-48 object-cover"
                                @error="onImageError($event)" />
                            <div
                                class="absolute bottom-0 p-2 flex items-start justify-center w-full bg-[#f8ffe2] bg-opacity-50">
                                <h5 class="text-black font-semibold text-base">{{ subject.name }}</h5>
                            </div>
                        </a>
                        <a href="#"
                            class="bg-[#96bd20] text-white text-sm py-1.5 px-4 text-center hover:bg-[#e87000] rounded-tl-sm rounded-tr-sm rounded-bl-2xl rounded-br-2xl overflow-hidden"
                            style="margin-top: 10px;">
                            Find Courses
                        </a>
                    </div>
                </template>

                <template v-else>
                    <div v-for="n in 12" :key="n"
                        class="animate-pulse bg-white flex flex-col rounded-2xl py-1 px-1 space-y-0">
                        <div class="w-full h-49 bg-gray-200 rounded-bl-md rounded-br-md rounded-tl-2xl rounded-tr-2xl">
                        </div>
                        <div class="h-8 bg-gray-300 rounded w-full rounded-tl-sm rounded-tr-sm rounded-bl-2xl rounded-br-2xl overflow-hidden"
                            style="margin-top: 10px;"></div>
                    </div>
                </template>
            </div>


            <div class="mt-8 flex justify-center pt-10" v-if="totalPages > 1">
                <ul class="flex items-center space-x-2">
                    <li :class="[
                        'page-item rounded-lg border border-[#dee2e6] p-3',
                        currentPage === 1 ? 'opacity-50 pointer-events-none' : ''
                    ]" style="margin-right: 10px;" @click="fetchSubjects(currentPage - 1)">
                        <a class="page-link text-[#e87000]" href="javascript:void(0)">« Previous</a>
                    </li>
                    <li v-for="page in totalPages" :key="page" @click="fetchSubjects(page)" :class="[
                        'cursor-pointer p-3 rounded-lg border border-[#dee2e6]',
                        currentPage === page ? 'bg-[#96bd20] text-white' : 'bg-white text-[#e87000] hover:bg-gray-100'
                    ]" style="margin-right: 10px;">
                        {{ page }}
                    </li>
                    <li :class="[
                        'page-item rounded-lg border border-[#dee2e6] p-3',
                        currentPage === totalPages ? 'opacity-50 pointer-events-none' : ''
                    ]" @click="fetchSubjects(currentPage + 1)">
                        <a class="page-link text-[#e87000]" href="javascript:void(0)">Next »</a>
                    </li>
                </ul>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const subjects = ref([])
const currentPage = ref(1)
const totalPages = ref(1)
const loading = ref(false)

const defaultImage = 'https://www.ehlweb.theskyroute.com/assets/front/course-finder-img/subject-area-not-found.png'

const slugify = (text) => {
  return text
    .toString()
    .toLowerCase()
    .trim()
    .replace(/\s+/g, '-')
    .replace(/[^\w\-]+/g, '')
    .replace(/\-\-+/g, '-')
}

const onImageError = (event) => {
  event.target.src = defaultImage
}

const fetchSubjects = async (page = 1) => {
  loading.value = true
  currentPage.value = page

  try {
    const res = await fetch(`https://www.ehlcrm.theskyroute.com/api/test/popular-subject-area?page=${page}`)
    const data = await res.json()

    subjects.value = data.rows.data.map((item) => {
      const slug = slugify(item.subject_area)
      return {
        id: item.id,
        name: item.subject_area,
        image: item.photo || defaultImage,
        // detailUrl: `https://www.ehlweb.theskyroute.com/subject-area/${item.id}/${slug}`,
      }
    })

    totalPages.value = data.rows.last_page
  } catch (err) {
    console.error('Error fetching subjects:', err)
  } finally {
    loading.value = false
  }
}

onMounted(() => {
  fetchSubjects()
})
</script>

<style scoped>
.popular-subject {
    background-color: #f9fafb;
}

@keyframes shimmer {
    0% {
        background-position: -400px 0;
    }

    100% {
        background-position: 400px 0;
    }
}

.shimmer {
    background: linear-gradient(to right, #eeeeee 8%, #dddddd 18%, #eeeeee 33%);
    background-size: 800px 104px;
    animation: shimmer 1.2s infinite linear;
}
</style>

<style scoped>
.popular-subject {
    background-color: #f9fafb;
}
</style>
