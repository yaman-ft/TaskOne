<script setup>
const isMenuOpen = ref(false);

const features = [
  {
    Image: "/_nuxt/assets/conect2.png",
    title: "Conect",
    description: "Real-time data visualization and business insights",
  },
  {
    Image: "/_nuxt/assets/collect.png",
    title: "Collect",
    description: "Smart workflows to save you time and effort",
  },
  {
    Image: "/_nuxt/assets/convert.png",
    title: "convert",
    description: "Military-grade encryption for your data",
  },
];

const TwoSection = [
  {
    Image: "/_nuxt/assets/lock.png",
    title: "Fully Secured",
    description:
      " Lorem ipsum dolor sit amet consectetur, adipisicing elit. Error dolor",
  },
  {
    Image: "/_nuxt/assets/lock.png",
    title: "Management",
    description:
      " deleniti animi voluptate amet eum nulla, facilis repellat? Itaque error nisi",
  },
  {
    Image: "/_nuxt/assets/lock.png",
    title: "Fully Secured",
    description:
      "  voluptates eos earum est excepturi enim nemo facere nostrum.",
  },
  {
    Image: "/_nuxt/assets/analysis.png",
    title: "Fully Secured",
    description:
      "  voluptates eos earum est sectetur, adipisicing elit. Error dolor",
  },
];
</script>

<template>
  <Head>
    <Title>
      SaaS
    </Title>
  </Head>
  <div class="min-h-screen overflow-hidden bg-white dark:bg-gray-900 transation-all duration-400">
    <div
      class="w-full h-180 bg-blue-200 dark:bg-gray-600 z-0 relative overflow-visible"
      style="clip-path: polygon(0 0, 100% 0, 100% 100%, 0 90%)"
    >
      <div
        class="w-full h-170 bg-gradient-to-r from-purple-500 to-indigo-400  dark:from-purple-900 absolute top-0 left-0 relative"
        style="clip-path: polygon(0 0, 100% 0, 100% 90%, 0 100%)"
      >
        <div
          class="w-40 h-40 bg-white rounded-full absolute top-30 left-175 shadow-xl"
        ></div>
      </div>
    </div>

    <div class="z-20 absolute top-0 left-0 right-0 w-full">
      <nav class="container mx-auto px-6 py-4 relative">
        <div class="flex items-center justify-between px-6">
          <div class="flex items-center space-x-2">
            <span class="text-xl font-bold text-white">Mern</span>
          </div>

          <div class="md:visible hidden md:flex items-center space-x-10">
            <a href="#" class="text-white hover:text-stone-400">Features</a>
            <a href="#" class="text-white hover:text-stone-400">Pricing</a>
            <a href="#" class="text-white hover:text-stone-400">Resources</a>
            <a href="#" class="text-white hover:text-stone-400">Company</a>
          </div>

          <div class="md:visible hidden md:flex items-center space-x-4">
            <TransMode />
            <button class="px-4 py-2 text-white border-1 rounded-lg px-2 hover:text-indigo-500 hover:bg-white">
              Log in
            </button>
            <button
              class="px-6 py-2 bg-white text-blue-500 rounded-lg hover:bg-blue-700 hover:text-white transition"
            >
              sign up
            </button>
          </div>

          <button
            @click="isMenuOpen = !isMenuOpen"
            class="md:hidden text-gray-600"
          >
            <svg
              class="w-6 h-6"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16m-7 6h7"
              ></path>
            </svg>
          </button>
        </div>

        <div v-if="isMenuOpen" class="md:hidden mt-4 space-y-4 py-4 border-t border-white absolute backdrop-blur-sm w-3/4  mx-auto">
          <TransMode class="mx-auto"/>
          <a href="#" class="block text-gray-800 dark:text-white hover:text-blue-600"
            >Features</a
          >
          <a href="#" class="block text-gray-800 dark:text-white hover:text-blue-600"
            >Pricing</a
          >
          <a href="#" class="block text-gray-800 dark:text-white hover:text-blue-600"
            >Resources</a
          >
          <a href="#" class="block text-gray-800 dark:text-white hover:text-blue-600"
            >Company</a
          >
          <div class="pt-4 space-y-2">
            <button
              class="w-full px-4 py-2 text-gray-800 dark:text-white dark:border-white hover:text-blue-600 border rounded"
            >
              Log in
            </button>
            <button
              class="w-full px-4 py-2 bg-white text-dark dark:text-white dark:bg-indigo-500 rounded-lg hover:bg-blue-700 transition"
            >
              sign up
            </button>
          </div>
        </div>
      </nav>

      <section class="container mx-auto px-6 py-16 md:py-24">
        <div class="flex flex-col md:flex-row items-center">
          <div class="lg:w-1/2 w-full text-center lg:text-start mb-12 md:mb-0">
            <h1
              class=" md:text-5xl text-6xl font-bold text-white text-center lg:text-left w-full leading-tight mb-6"
            >
              SaaS Delivery Management Software
            </h1>
            <p class="lg:text-lg text-white mb-8 text-xl leading-9">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Esse
              corporis fugiat quia quas, ab ea at, deleniti omnis itaque porro
              amet officiis aut facere, doloremque nemo animi harum temporibus
              quo.
            </p>
            <div
              class="flex flex-row justify-center lg:justify-start  space-y-0 space-x-4"
            >
              <button
                class="px-8 py-3 bg-white text-indigo-500 rounded-lg hover:bg-indigo-500 hover:text-white transition"
              >
                Get Started
              </button>
              <button
                class="px-8 py-3 border border-white text-white rounded-lg hover:bg-gray-50 hover:text-indigo-500 transition"
              >
                Watch Now
              </button>
            </div>
          </div>
          <div class="md:w-1/2">
            <div
              class="bg-white rounded-2xl aspect-video flex items-center  justify-center shadow-xl lg:visible invisible "
            >
              <DashBoard class="w-full h-full rounded-2xl  lg:visible invisible " />
            </div>
          </div>
        </div>
      </section>
    </div>

    <section class="bg-gray-50 md:py-12 dark:bg-gray-900 py-20 my-20 md:my-0">
      <div class="container mx-auto px-6 dark:bg-gray-900 dark:text-white">
        <p class="text-center mb-8">COMPANIES WE HAVE HELPED GROW</p>
        <div class="flex flex-wrap w-3/4 mx-auto justify-around gap-8 md:gap-8">
          <div class="h-10 w-30 m-1 text-gray-400">
            <img class="w-full h-full" src="@/assets/aven.png" alt="" />
          </div>
          <div class="h-10 w-30 m-1 text-gray-400">
            <img class="w-full h-full" src="@/assets/idea.jpg" alt="" />
          </div>
          <div class="h-10 w-30 m-1 text-gray-400">
            <img class="w-full h-full" src="@/assets/velocity.jpg" alt="" />
          </div>
          <div class="h-10 w-30 m-1 text-gray-400">
            <img class="w-full h-full" src="@/assets/leva.webp" alt="" />
          </div>
          <div class="h-10 w-30 m-1 text-gray-400">
            <img class="w-full h-full" src="@/assets/treva.png" alt="" />
          </div>
        </div>
      </div>
    </section>

    <section class="container mx-auto px-6 py-16 md:py-24 dark:text-white">
      <div class="text-center mb-16">
        <h2 class="text-3xl font-bold text-gray-900 mb-4 dark:text-white">
          Learn more about process
        </h2>
        <p class="text-lg text-gray-600 max-w-2xl mx-auto dark:text-white">
          Our platform provides all the tools your team needs to work
          efficiently and effectively.
        </p>
      </div>

      <div
        class="flex md:flex-cols-8 md:flex-row flex-col flex-wrap flex-col justify-center gap-8 mt-40 bg-white relative dark:bg-gray-900"
      >
      <div class="absolute w-100 h-100 border-t-2 border-dashed border-indigo-500 rounded-full left-98 -top-20 2xl:visible invisible"></div>
      <div class="absolute w-100 h-100 border-t-2 border-dashed border-indigo-500 rounded-full right-90 -top-20 2xl:visible invisible"></div>

        <div
          v-for="(feature, index) in features"
          :key="index"
          class="bg-white dark:bg-gray-800 dark:text-white mx-auto lg:mx-0 p-6 h-80 w-70 rounded-2xl shadow-sm transition duration-300 ease-in-out transition-all hover:border-b-8 dark:border-indigo-800 border-indigo-400 relative"
        >
          <div
            class="h-3 w-3 dark:bg-gray-500 rounded-full border-indigo-400 border-3 p-6 grid content-center bg-white absolute text-indigo-300 -top-6 left-30 text-lg"
          >
            {{ index + 1 }}
          </div>
          <div class="text-4xl mb-4">
            <img class="w-40 h-30 mx-auto my-6" :src="feature.Image" alt="" />
          </div>
          <h3 class="text-xl font-semibold mb-2 my-2 mx-auto text-center">
            {{ feature.title }}
          </h3>
          <p class="text-gray-600 dark:text-white my-2 mx-auto text-center">{{ feature.description }}</p>
        </div>
      </div>
    </section>

    <section class="text-dark dark:text-white py-16 md:py-24 relative overflow-hidden">
      <div
        class="absolute w-60 h-60 bg-gradient-to-r from-purple-500 to-indigo-400 dark:from-purple-900 rounded-full top-0 -left-40"
      ></div>

      <div class="container mx-auto px-6">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold mb-4">
            Start today with free premium plan
          </h2>
          <p class="max-w-2xl mx-auto">
            Don't just take our word for it. Here's what our customers have to
            say about our platform.
          </p>
        </div>

        <div
          class="flex md:flex-cols-2 flex-col xl:flex-row gap-8 justify-center mx-auto items-center"
        >
          <div
            class="lg:w-140 lg:h-100 w-120 h-100 dark:from-gray-700 dark:bg-gradient-to-r to-gray-400 rounded-3xl bg-white p-4 md:inline block shadow-md"
          >
            <div class="flex justify-around p-1 dark:text-white">
              <div class="flex flex-col justify-between h-full gap-4 w-1/2">
                <button
                  class="rounded-2xl outline-1 dark:text-white outline-indigo-500 lg:w-30 w-20 text-xs text-indigo-500 h-10 hover:bg-indigo-500 hover:text-white transation-all duration-200"
                >
                  BASIC PLAN
                </button>
                <span class="text-zinc-600 dark:text-white"
                  ><span class="text-5xl font-bold dark:text-white text-stone-950">$0</span> per
                  month</span
                >
                <span class="lg:text-sm text-xs leading:6 lg:leading-8 text-zinc-600 dark:text-white">
                  Only the other hand Lorem ipsum dolor, sit amet consectetur
                  adipisicing elit. Cupiditate nemo minima quae aperiam deleniti
                  Lorem ipsum, dolor sit amet consectetur adipisicing elit.
                  Deleniti iusto nam illum dolor tempora quaerat
                </span>
                <button
                  class="px-4 py-2 text-xs text-white rounded-xl bg-indigo-500 lg:w-30 w-20 h-10"
                >
                  join now
                </button>
              </div>
              <div class="h-full flex justify-center items-center self-center">
                <ul class="list-image-[url(@/assets/indigoicon.png)]">
                  <li class="leading-10 my-1 mx-1">Limited access library</li>
                  <li class="leading-10 my-1 mx-1">comercial license</li>
                  <li class="leading-10 my-1 mx-1">Hotline support 24/7</li>
                  <li class="leading-10 my-1 mx-1">300 + HTML UI Elements</li>
                  <li class="leading-10 my-1 mx-1">EaCommerce builder</li>
                </ul>
              </div>
            </div>
          </div>
          <div
            class="lg:w-140 lg:h-100 w-120 h-100 rounded-3xl bg-gradient-to-r from-purple-500 to-indigo-400 dark:from-purple-900 text-white p-4 shadow-xl"
          >
            <div class="flex justify-around p-1">
              <div class="flex flex-col justify-between h-full gap-4 w-1/2">
                <button
                  class="rounded-2xl outline-1 outline-white lg:w-30 w-20 text-xs text-white h-10 hover:bg-white hover:text-indigo-500 transation-all duration-200"
                >
                  PREMIUM PLAN
                </button>
                <span
                  ><span class="text-5xl font-bold">$99</span> per month</span
                >
                <span class="lg:text-sm text-xs leading:6 lg:leading-8">
                  Only the other hand Lorem ipsum dolor, sit amet consectetur
                  adipisicing elit. Cupiditate nemo minima quae aperiam deleniti
                  Lorem ipsum, dolor sit amet consectetur adipisicing elit.
                  Deleniti iusto nam illum dolor tempora quaerat
                </span>
                <button
                  class="px-4 py-2 text-xs text-indigo-500 rounded-xl bg-white lg:w-30 w-20 h-10"
                >
                  join now
                </button>
              </div>
              <div class="h-full flex justify-center items-center self-center">
                <ul class="list-image-[url(@/assets/whiteicon.png)]">
                  <li class="leading-10 my-1 mx-1">Limited access library</li>
                  <li class="leading-10 my-1 mx-1">comercial license</li>
                  <li class="leading-10 my-1 mx-1">Hotline support 24/7</li>
                  <li class="leading-10 my-1 mx-1">300 + HTML UI Elements</li>
                  <li class="leading-10 my-1 mx-1">EaCommerce builder</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section
      class="container mx-auto w-full h-auto my-8 relative overflow-hidden dark:text-white"
    >
      <div
        class="absolute w-60 h-60 bg-gradient-to-r from-purple-500 to-indigo-400 dark:from-purple-900 rounded-full bottom-0 -right-40"
      ></div>
      <div class="mx-auto text-center">
        <h2 class="text-3xl font-bold mb-4">Features For you</h2>
        <p class="text-zinc-800 dark:text-white mb-8">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Incidunt aut,
          eum recusandae provident .
        </p>
        <div class="flex flex-wrap justify-center gap-4">
          <div
            v-for="(items, index) in TwoSection"
            :key="index"
            class="bg-white  dark:border-indigo-800 dark:bg-gray-800 dark:text-white p-6 h-80 w-70 rounded-2xl shadow-sm transition duration-300 ease-in-out transition-all hover:border-b-8 border-indigo-400 relative"
          >
            <div class="text-4xl mb-4">
              <img
                class="w-30 border-1 border-indigo-500 rounded-2xl h-30 mx-auto my-6 relative"
                :src="items.Image"
                alt=""
              />
              <div
                class="absolute w-4 h-4 bg-white  dark:bg-gray-900 dark:text-white rounded-full border-1 border-indigo-500 flex items-center justify-center top-10 left-47"
              >
                <div class="absolute bg-gradient-to-r from-purple-500 to-indigo-400 dark:from-purple-900 w-2 h-2 rounded-full"></div>
              </div>
            </div>
            <h3 class="text-xl font-semibold mb-2 my-2 mx-auto">
              {{ items.title }}
            </h3>
            <p class="text-gray-600 dark:text-white my-2 mx-auto">{{ items.description }}</p>
          </div>
        </div>
      </div>
      <button
        class="w-40 h-12 mx-auto block text-white mt-40 py-3 px-4 bg-gradient-to-r from-purple-500 to-indigo-400 dark:from-purple-900 text-sm hover:bg-indigo-300 transation-all duration-300 rounded-xl"
      >
        Explore Feature
      </button>
    </section>
    <section class="w-full my-10 dark:bg-gray-900">
      <SlideSection />
    </section>
    <section class="w-full">
      <div
        class="w-3/4 bg-gradient-to-r from-purple-500 to-indigo-400 dark:from-purple-900 rounded-2xl mx-auto p-15 relative overflow-hidden"
      >
        <span class="text-3xl text-white font-bold my-4 block"
          >Sign Up and get started</span
        >
        <span class="text-sm text-white block"
          >free trail 14 days of change and without obligation</span
        >
        <input
          class="lg:w-2/4 w-full rounded-lg p-2 bg-white/50 backdrop-invert backdrop-opacity-10 my-4 placeholder-stone-50"
          placeholder="enter your email here"
          type="text"
        />
        <button class="rounded-lg bg-white text-indigo-500 lg:mx-1.5 mx-auto p-2 text-sm">
          Register for free
        </button>
        <div
          class="absolute w-80 h-80 bg-white/50 backdrop-invert backdrop-opacity-10 rounded-full -top-40 right-10 shadow-xl"
        ></div>
        <div
          class="absolute w-80 h-80 bg-white/50 backdrop-invert backdrop-opacity-10 rounded-full -bottom-20 -right-40 shadow-xl"
        ></div>
        <div
          class="absolute w-80 h-80 bg-white/50 backdrop-invert backdrop-opacity-10 rounded-full -bottom-30 right-20 shadow-xl"
        ></div>
      </div>
    </section>
    <section class="w-full my-20 dark:text-white">
      <span class="block text-center text-3xl font-bold my-4"
        >do you have any quistion</span
      >
      <span class="block text-center text-sm text-gray-600 dark:text-white"
        >our support team ready to help you , please contact with them</span
      >
      <CollapseSection class="w-2/4 rounded-lg shadow-lg p-20" />
      <button
        class="w-40 h-12 mx-auto block text-white mt-40 py-3 px-4 bg-gradient-to-r from-purple-500 to-indigo-400 dark:from-purple-900 text-sm hover:bg-indigo-300 transation-all duration-300 rounded-xl"
      >
        more FAQs
      </button>
    </section>

    <footer class="bg-white text-gray-600 dark:bg-gray-900 dark:text-white py-12 relative">
      <div
        class="absolute w-60 h-60 bg-gradient-to-r from-purple-500 to-indigo-400 dark:from-purple-900 rounded-full -top-80 -left-30"
      ></div>
      <div class="container mx-auto px-6">
        <div class=" flex justify-around gap-4 flex-col lg:flex-row mb-8">
          <div class="lg:w-1/4 w-full">
            <div class="flex items-center space-x-2 mb-4">
              <span class="text-xl font-bold text-indigo-500">Mern</span>
            </div>
            <p class="text-gray-400">
              The standard Chunk Lorem ipsum dolor sit amet, consectetur
              adipisicing elit. Eveniet dolorem impedit consequuntur eo
            </p>
          </div>

          <div class=" flex flex-col justify-around lg:flex-row flex-wrap my-3 w-3/4">
            <div>
            <h3 class="font-semibold mb-4 text-indigo-500">Product</h3>
            <ul class="space-y-2 text-gray-400">
              <li><a href="#" class="hover:text-white">Features</a></li>
              <li><a href="#" class="hover:text-white">Pricing</a></li>
              <li><a href="#" class="hover:text-white">Integrations</a></li>
            </ul>
          </div>

          <div>
            <h3 class="font-semibold mb-4 text-indigo-500">Company</h3>
            <ul class="space-y-2 text-gray-400">
              <li><a href="#" class="hover:text-white">About</a></li>
              <li><a href="#" class="hover:text-white">Careers</a></li>
              <li><a href="#" class="hover:text-white">Contact</a></li>
            </ul>
          </div>

          <div>
            <h3 class="font-semibold mb-4 text-indigo-500">Resources</h3>
            <ul class="space-y-2 text-gray-400">
              <li><a href="#" class="hover:text-white">Blog</a></li>
              <li><a href="#" class="hover:text-white">Help Center</a></li>
              <li><a href="#" class="hover:text-white">Webinars</a></li>
            </ul>
          </div>
            <div>
            <h3 class="font-semibold mb-4 text-indigo-500">Contact</h3>
            <ul class="space-y-2 text-gray-400">
              <li><a href="#" class="hover:text-white">Blog</a></li>
              <li><a href="#" class="hover:text-white">Help Center</a></li>
              <li><a href="#" class="hover:text-white">Webinars</a></li>
            </ul>
          </div>
          </div>
        </div>
      </div>
    </footer>
    
            <div class="w-full flex py-9 px-2 flex-col lg:flex-row gap-10 justify-between bg-gradient-to-r from-purple-500 to-indigo-400 dark:from-purple-900 text-sm text-white">
              <p class="lg:my-0 my-3">© 2022</p>
              <div class="flex w-1/4 justify-center gap-8">
                <span>FAQ</span>
                <span>Terms</span>
                <span>privacy and policy</span>
    
              </div>
            </div>
  </div>
</template>
