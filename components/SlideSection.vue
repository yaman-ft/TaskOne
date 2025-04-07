<template>
  <div class="bg-[#f4f8fc] py-10 px-4 text-center dark:bg-gray-800 dark:text-white">
    <h2 class="text-2xl md:text-3xl font-bold text-gray-800 mb-2 dark:text-white">Check what our clients are saying</h2>
    <p class="text-gray-500 mb-8 dark:text-white">Cum soluta nobis est eligendi optio cumque</p>

    <div class="relative max-w-2xl mx-auto overflow-hidden min-h-[250px] dark:bg-gray-800">
      <transition-group
        tag="div"
        name="slide-fade"
        class="relative"
      >
        <div
          v-for="(testimonial, i) in testimonials"
          :key="i"
          v-show="i === currentIndex"
          class="absolute  inset-0 transition-transform duration-500 ease-in-out"
        >
        <div  class="bg-white rounded-xl shadow-md p-6 md:p-8 dark:bg-gray-900">
              <div class="text-yellow-400 text-lg mb-3">★★★★★</div>
         
            <p class="text-gray-700 dark:text-white text-base mb-4">
                {{ testimonial.text }}
            </p>
           
                <img class="w-20 my-2 mx-auto h-15" :src="testimonial.image" alt="">
          </div>
        </div>
      </transition-group>
    </div>

    <div class="mt-6 flex justify-center space-x-2">
      <span
        v-for="(dot, i) in testimonials"
        :key="i"
        class="w-3 h-3 rounded-full cursor-pointer"
        :class="i === currentIndex ? 'bg-indigo-700' : 'bg-indigo-400'"
        @click="goToSlide(i)"
      ></span>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'TestimonialSlider',
  data() {
    return {
      currentIndex: 0,
      interval: null,
      testimonials: [
        {
          name: 'Cristofer Vaccaro',
          title: 'CEO PT Aven',
          text: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Nam, adipisci nostrum accusantium aperiam iste at dolorem nemo expedita dignissimos, facere error voluptas quia accusamus delectus. Quisquam quia repellat illo quam!',
          image: '/_nuxt/assets/aven.png',
        },
        {
          name: 'Jane Doe',
          title: 'Marketing Manager',
          text: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Nam, adipisci nostrum accusantium aperiam iste at dolorem nemo expedita dignissimos, facere error voluptas quia accusamus delectus. Quisquam quia repellat illo quam!',
          image: '/_nuxt/assets/idea.jpg',
          },
         {
          name: 'Jane Doe',
          title: 'Marketing Manager',
          text: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Nam, adipisci nostrum accusantium aperiam iste at dolorem nemo expedita dignissimos, facere error voluptas quia accusamus delectus. Quisquam quia repellat illo quam!',
          image: '/_nuxt/assets/velocity.jpg',
        }, {
          name: 'Jane Doe',
          title: 'Marketing Manager',
          text: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Nam, adipisci nostrum accusantium aperiam iste at dolorem nemo expedita dignissimos, facere error voluptas quia accusamus delectus. Quisquam quia repellat illo quam!',
          image: '/_nuxt/assets/leva.webp',
        }, {
          name: 'Jane Doe',
          title: 'Marketing Manager',
          text: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Nam, adipisci nostrum accusantium aperiam iste at dolorem nemo expedita dignissimos, facere error voluptas quia accusamus delectus. Quisquam quia repellat illo quam!',
          image: '/_nuxt/assets/treva.png',
        },
      ],
    };
  },
  mounted() {
    this.startSlider();
  },
  beforeUnmount() {
    clearInterval(this.interval);
  },
  methods: {
    startSlider() {
      this.interval = setInterval(() => {
        this.currentIndex = (this.currentIndex + 1) % this.testimonials.length;
      }, 5000);
    },
    goToSlide(index) {
      this.currentIndex = index;
    },
  },
};
</script>

<style scoped>
.slide-fade-enter-active, .slide-fade-leave-active {
  transition: all 1s ease;
}
.slide-fade-enter-from {
  opacity: 0;
  transform: translateX(100%);
}
.slide-fade-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}
</style>
