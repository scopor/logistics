<template>
  <teleport to="body">
    <transition name="modal">
      <div v-if="show" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4" id="photoPrint" @click="closeModal">
        <div class="relative bg-white rounded-sm shadow-xl max-w-[90vw] max-h-[90vh] overflow-hidden group" @click.stop>
          <button @click="$emit('close')" class="absolute top-2 right-2 text-gray-500 hover:text-gray-700 hidden group-hover:block z-10" id="closeButton">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
          <div class="bg-white p-8 pb-6 flex items-center justify-center" style="width: auto; height: 80vh;">
            <img :src="imageUrl" :alt="imageAlt" class="max-w-full max-h-full object-contain rounded-md" />
          </div>
          <div class="flex bg-opacity-50 py-8 justify-center items-center text-sm space-x-2">
            <span>{{ imageAlt }}</span><span> photo by {{ photographer }}</span>
          </div>
          <button
              @click="$emit('prev')"
              class="absolute left-4 top-1/2 transform -translate-y-1/2 bg-white bg-opacity-50 hover:bg-opacity-75 rounded-full p-2 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-500 hidden group-hover:block"
              aria-label="Previous image"  id="prevButton"
          >
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
            </svg>
          </button>
          <button
              @click="$emit('next')"
              class="absolute right-4 top-1/2 transform -translate-y-1/2 bg-white bg-opacity-50 hover:bg-opacity-75 rounded-full p-2 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-500 hidden group-hover:block"
              aria-label="Next image" id="nextButton"
          >
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
            </svg>
          </button>
        </div>
      </div>
    </transition>
  </teleport>
</template>

<script setup>
defineProps({
  show: Boolean,
  imageUrl: String,
  imageAlt: String,
  photographer: String,
})

const emit = defineEmits(['close', 'prev', 'next'])

const closeModal = (event) => {
  if (event.target === event.currentTarget) {
    emit('close')
  }
}
</script>

<style scoped>
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.1s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}

@media print {
  body * {
    visibility: hidden;
  }
  #navBar, #navBar * {
    visibility: hidden;
  }
  #closeButton, #closeButton * {
    visibility: hidden;
  }
  #prevButton, #prevButton * {
    visibility: hidden;
  }
  #nextButton, #nextButton * {
    visibility: hidden;
  }
  #photoPrint {
    visibility: visible;
  }
}
</style>
