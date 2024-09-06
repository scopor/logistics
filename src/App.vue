<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-900 to-gray-800 text-white">
    <header class="py-20 px-4 sm:px-6 lg:px-8">
      <h1 class="text-3xl font-thin text-center hover:text-pink-400">Vinlane Photo Gallery</h1>
    </header>
    <main class="container mx-auto px-4 sm:px-6 lg:px-8 py-8">
      <div v-if="loading" class="text-center">
        <div class="inline-block animate-spin rounded-full h-8 w-8 border-t-2 border-b-2 border-white"></div>
        <p class="mt-2">Loading photos...</p>
      </div>
      <div v-else-if="error" class="text-center text-red-500">
        {{ error }}
      </div>
      <div v-else>
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
          <div v-for="photo in photos" :key="photo.id" class="group">
            <div
                class="relative overflow-hidden rounded-lg shadow-lg transition-transform duration-300 ease-in-out transform hover:scale-105 cursor-pointer"
                @click="openModal(photo)"
            >
              <img :src="photo.urls.regular" :alt="photo?.description" class="w-full h-64 object-cover" />
              <div class="absolute inset-0 bg-black bg-opacity-50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
                <p class="text-white text-center px-4">{{ photo.description }}</p>
              </div>
            </div>
          </div>
        </div>

        <div class="mt-12 flex justify-center">
          <button
              @click="prevPage"
              :disabled="currentPage === 1"
              class="px-4 py-2 bg-gray-700 text-white rounded-l-md hover:bg-gray-600 disabled:opacity-50 disabled:cursor-not-allowed"
          >
            Previous
          </button>
          <span class="px-4 py-2 bg-gray-600 text-white">{{ currentPage }} / {{ totalPages }}</span>
          <button
              @click="nextPage"
              :disabled="currentPage === totalPages"
              class="px-4 py-2 bg-gray-700 text-white rounded-r-md hover:bg-gray-600 disabled:opacity-50 disabled:cursor-not-allowed"
          >
            Next
          </button>
        </div>
      </div>
    </main>
    <footer class="py-6 px-4 sm:px-6 lg:px-8 text-center text-gray-400">
      <p>&copy; 2024 Vinlane Photo Gallery. All rights reserved.</p>
    </footer>

    <PhotoModal
        :show="showModal"
        :image-url="selectedPhoto?.urls.full || ''"
        :image-alt="selectedPhoto?.description || ''"
        :photographer="selectedPhoto?.user.name || ''"
        @close="closeModal"
        @prev="prevImage"
        @next="nextImage"
    />
  </div>
</template>

<script setup lang="ts">
import {computed, onMounted, ref} from 'vue'
import PhotoModal from '@/components/PhotoModal.vue'

interface UnsplashPhoto {
  id: string;
  urls: {
    full: string;
    regular: string;
  };
  description: string;
  user: {
    name: string;
    total_photos: number;
  };
}

const photos = ref<UnsplashPhoto[]>([])
const loading = ref(true)
const error = ref<string | null>(null)
const showModal = ref(false)
const selectedPhoto = ref<UnsplashPhoto | null>(null)
const currentPage = ref(1)
const perPage = 12

const fetchPhotos = async () => {
  const UNSPLASH_ACCESS_KEY = import.meta.env.VITE_UNSPLASH_ACCESS_KEY;
  const apiUrl = `https://api.unsplash.com/users/scopor/photos?page=${currentPage.value}&per_page=${perPage}&client_id=${UNSPLASH_ACCESS_KEY}`

  try {
    const response = await fetch(apiUrl)
    if (!response.ok) {
      photos.value = []
    }
    photos.value = await response.json()
  } catch (err) {
    console.error('Error:', err)
    photos.value = []
  } finally {
    loading.value = false
  }
}

const totalPages = computed(() => Math.ceil((photos && photos.value[0] ? photos.value[0].user.total_photos : 0) / perPage))

const nextPage = () => {
  if (currentPage.value < totalPages.value) {
    currentPage.value++
    fetchPhotos()
  }
}

const prevPage = () => {
  if (currentPage.value > 1) {
    currentPage.value--
    fetchPhotos()
  }
}

const openModal = (photo: any) => {
  selectedPhoto.value = photo
  showModal.value = true
}

const closeModal = () => {
  showModal.value = false
  selectedPhoto.value = null
}

const prevImage = () => {
  const currentIndex = photos.value.findIndex(photo => photo.id === selectedPhoto.value!.id)
  if (currentIndex > 0) {
    selectedPhoto.value = photos.value[currentIndex - 1]
  } else {
    selectedPhoto.value = photos.value[photos.value.length - 1]
  }
}

const nextImage = () => {
  const currentIndex = photos.value.findIndex(photo => photo.id === selectedPhoto.value!.id)
  if (currentIndex < photos.value.length - 1) {
    selectedPhoto.value = photos.value[currentIndex + 1]
  } else {
    selectedPhoto.value = photos.value[0]
  }
}

onMounted(fetchPhotos)
</script>
