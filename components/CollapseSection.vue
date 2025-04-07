<template>
  <div class="w-full max-w-5xl mx-auto my-4 dark:bg-gray-800">
    <div v-for="(item, index) in faqs" :key="index" class="py-4">
      <button
        @click="toggle(index)"
        class="w-full text-left text-lg font-medium flex justify-left gap-8 items-center focus:outline-none"
      >
        <svg
          :class="{ 'rotate-180': activeIndex === index }"
          class="lg:w-4 lg:h-4 w-3 h-3 text-white bg-indigo-500 rounded-full transform transition-transform duration-300"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M19 9l-7 7-7-7"
          />
        </svg>
        {{ item.question }}
      </button>

      <!-- transition effect -->
      <transition name="collapse">
        <div
          v-show="activeIndex === index"
          class="mt-2 text-gray-600 overflow-hidden"
        >
          <div class="py-2 text-gray-500 text-left leading-8">
            {{ item.answer }}
          </div>
        </div>
      </transition>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "FaqCollapse",
  data() {
    return {
      activeIndex: null,
      faqs: [
        {
          question: "Website response taking time, how to improve?",
          answer:
            "Get your blood tests delivered at the home collect a sample from  management news Mollitia enim  laboriosam reprehenderit velit! Illo nihil placeat totam. Laborum fugit rerum maiores at expedita, tempore quis nostrum, a ullam magni repellendus",
        },
        {
          question:
            "App installation failed, how to update system information?",
          answer:
            "You can update the system info from the settings tab in your dashboard. Mollitia enim    laboriosam reprehenderit velit! Illo nihil placeat totam. Laborum fugitrerum maiores at expedita, tempore quis nostrum, a ullam magni repellendus",
          },
        {
          question:
            "App installation failed, how to update system information?",
          answer:
            "You can update the system info from the settings tab in your dashboard. Mollitia enim    laboriosam reprehenderit velit! Illo nihil placeat totam. Laborum fugitrerum maiores at expedita, tempore quis nostrum, a ullam magni repellendus",
        },
        {
          question: "New update fixed all bug and issues?",
          answer: "Yes, the latest update   Mollitia enim   laboriosam reprehenderit velit! Illo nihil placeat totam. Laborum fugit  rerum maiores at expedita, tempore quis nostrum, a ullam magni repellendushas resolved all the known issues.",
        },
      ],
    };
  },
  methods: {
    toggle(index) {
      this.activeIndex = this.activeIndex === index ? null : index;
    },
  },
};
</script>

<style scoped>
/* Collapse animation */
.collapse-enter-active,
.collapse-leave-active {
  transition: all 0.3s ease-in-out;
  max-height: 200px;
  opacity: 1;
}
.collapse-enter,
.collapse-leave-to {
  max-height: 0;
  opacity: 0;
}
</style>
