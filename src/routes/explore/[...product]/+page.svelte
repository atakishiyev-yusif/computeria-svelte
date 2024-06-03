<script>
  import { page } from "$app/stores";
  import { onMount } from "svelte";
  import axios from "axios";

  import UserProfileCard from "../../../components/UserProfileCard.svelte";
  import CalendarIcon from "../../../components/icons/CalendarIcon.svelte";
  import HeartIcon from "../../../components/icons/HeartIcon.svelte";
  import Loader from "../../../components/Loader.svelte";

  let product = [];
  let slug;
  let images = [];
  let currentImage;
  let loading = false;

  const getProduct = async () => {
    try {
      loading = true;
      const response = await axios.get("https://dummyjson.com/products/");
      const data = response.data.products;
      product = data.find((item) => String(item.id) === slug);
      images = product.images;
      currentImage = product.images.at(0);
    } catch (error) {
      console.log(error);
    } finally {
      loading = false;
    }
  };

  onMount(async () => {
    slug = $page.params.product;
    await getProduct();
  });

  $: console.log(product);
</script>

{#if loading}
  <Loader />
{:else}
  <div class="bg-white">
    <div
      class="max-w-2xl mx-auto py-4 px-4 sm:py-12 sm:px-6 lg:max-w-7xl lg:px-8"
    >
      <div class="lg:grid lg:grid-cols-3 lg:gap-x-8 lg:items-start">
        <!-- Image gallery -->
        <div class="col-span-2 flex flex-col-reverse">
          <!-- Image selector -->
          <div
            class="hidden mt-6 w-full max-w-2xl mx-auto sm:block lg:max-w-none"
          >
            <div
              class="grid grid-cols-4 gap-6"
              aria-orientation="horizontal"
              role="tablist"
            >
              {#each images as image, index (index)}
                <button
                  id="tabs-1-tab-1"
                  class="relative h-24 bg-white rounded-md flex items-center justify-center text-sm font-medium uppercase text-gray-900 cursor-pointer hover:bg-gray-50 focus:outline-none focus:ring focus:ring-offset-4 focus:ring-opacity-50"
                  aria-controls="tabs-1-panel-1"
                  role="tab"
                  type="button"
                  on:click={() => {
                    currentImage = image;
                  }}
                >
                  <span class="absolute inset-0 rounded-md overflow-hidden">
                    <img
                      src={image}
                      alt=""
                      class="w-full h-full object-center object-cover"
                    />
                  </span>

                  <!-- Selected: "ring-indigo-500", Not Selected: "ring-transparent" -->
                  <span
                    class="ring-transparent absolute inset-0 rounded-md ring-2 ring-offset-2 pointer-events-none"
                    aria-hidden="true"
                  ></span>
                </button>
              {/each}

              <!-- More images... -->
            </div>
            <div class="mt-14 bg-gray-100 p-6 rounded-2xl">
              <h3 class="h3 text-gray-900">Açıqlama</h3>
              <p class="text-gray-700 mt-3">
                {product.description}
              </p>
            </div>
          </div>

          <div class="w-full min-h-[500px] flex items-center justify-center">
            <!-- Tab panel, show/hide based on tab state. -->
            <div
              id="tabs-1-panel-1"
              aria-labelledby="tabs-1-tab-1"
              role="tabpanel"
              tabindex="0"
              class="max-h-[500px] overflow-hidden"
            >
              <img
                src={currentImage}
                alt={product.title}
                class="object-center object-cover sm:rounded-lg"
              />
            </div>

            <!-- More images... -->
          </div>
        </div>

        <!-- Product info -->
        <div class="mt-10 px-4 sm:px-0 sm:mt-16 lg:mt-0">
          <div class="bg-gray-100 p-6 rounded-2xl">
            <div class="flex items-center justify-between">
              <h1 class="text-3xl font-extrabold tracking-tight text-gray-900">
                {product.title}
              </h1>
              <div class="opacity-70 hover:opacity-100">
                <HeartIcon />
              </div>
            </div>

            <div class="mt-3">
              <h2 class="sr-only">Product information</h2>
              <p class="text-3xl text-gray-900">₼{product.price}</p>
            </div>

            <!-- Reviews -->

            <div class="mt-6">
              <div class="flex items-center text-gray-700 gap-2">
                <CalendarIcon />
                <p>Yaradılma vaxtı: 30 may 2024</p>
              </div>
            </div>
          </div>

          <div class="p-6 bg-gray-100 mt-6 rounded-2xl">
            <UserProfileCard
              name="John Doe"
              mail="johndoe@gmail.com"
              imageSrc=""
            />

            <div class="mt-2">
              <div
                class="rounded-lg border border-gray-100 text-center shadow-xl"
              >
                <div class="px-6 py-5">
                  <p class="font-medium">Əlaqə</p>

                  <div class="mt-4 space-y-2">
                    <a
                      class="block rounded-full border border-green-400 px-8 py-3 text-sm font-medium text-green-400"
                      style="gap: 0.4rem;"
                      href="https://wa.me/994708445276"
                      target="_blank"
                    >
                      <div class="flex items-center justify-center gap-2">
                        <span
                          ><svg
                            xmlns="http://www.w3.org/2000/svg"
                            width="20"
                            height="20"
                            viewBox="0 0 24 24"
                            fill="none"
                            stroke="currentColor"
                            stroke-width="2"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            class="lucide lucide-message-circle-more"
                            ><path d="M7.9 20A9 9 0 1 0 4 16.1L2 22Z" /><path
                              d="M8 12h.01"
                            /><path d="M12 12h.01" /><path
                              d="M16 12h.01"
                            /></svg
                          ></span
                        >
                        <span class="text-sm"> Whatsapp </span>
                      </div>
                    </a>
                    <a
                      class="block text-sm rounded-full border border-gray-500 px-8 py-3 text-sm font-medium text-gray-600"
                      href="#"
                    >
                      <div
                        class="flex items-center justify-center gap-2 w-full"
                      >
                        <span>
                          <svg
                            xmlns="http://www.w3.org/2000/svg"
                            width="20"
                            height="20"
                            viewBox="0 0 24 24"
                            fill="none"
                            stroke="currentColor"
                            stroke-width="2"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            class="lucide lucide-phone-outgoing"
                            ><polyline points="22 8 22 2 16 2" /><line
                              x1="16"
                              x2="22"
                              y1="8"
                              y2="2"
                            /><path
                              d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"
                            /></svg
                          >
                        </span>
                        <span class="text-sm"> Zəng </span>
                      </div>
                    </a>
                  </div>

                  <p class="mt-4 inline-flex items-center gap-1.5">
                    <span
                      class="inline-block h-1.5 w-1.5 rounded-full bg-green-500"
                    ></span>
                    <span class="text-xs font-medium text-green-700">
                      Chat online
                    </span>
                  </p>
                </div>

                <div
                  class="flex justify-center gap-4 border-t border-gray-100 px-6 py-5"
                >
                  <a
                    href="#"
                    class="rounded-full border border-gray-200 p-2 text-gray-900"
                  >
                    <span class="sr-only">Company Facebook</span>
                    <svg
                      class="h-4 w-4"
                      fill="currentColor"
                      viewBox="0 0 24 24"
                      aria-hidden="true"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </a>

                  <a
                    href="#"
                    class="rounded-full border border-gray-200 p-2 text-gray-900"
                  >
                    <span class="sr-only">Company Instagram</span>
                    <svg
                      class="h-4 w-4"
                      fill="currentColor"
                      viewBox="0 0 24 24"
                      aria-hidden="true"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.902 4.902 0 01-1.153 1.772 4.902 4.902 0 01-1.772 1.153c-.636.247-1.363.416-2.427.465-1.067.048-1.407.06-4.123.06h-.08c-2.643 0-2.987-.012-4.043-.06-1.064-.049-1.791-.218-2.427-.465a4.902 4.902 0 01-1.772-1.153 4.902 4.902 0 01-1.153-1.772c-.247-.636-.416-1.363-.465-2.427-.047-1.024-.06-1.379-.06-3.808v-.63c0-2.43.013-2.784.06-3.808.049-1.064.218-1.791.465-2.427a4.902 4.902 0 011.153-1.772A4.902 4.902 0 015.45 2.525c.636-.247 1.363-.416 2.427-.465C8.901 2.013 9.256 2 11.685 2h.63zm-.081 1.802h-.468c-2.456 0-2.784.011-3.807.058-.975.045-1.504.207-1.857.344-.467.182-.8.398-1.15.748-.35.35-.566.683-.748 1.15-.137.353-.3.882-.344 1.857-.047 1.023-.058 1.351-.058 3.807v.468c0 2.456.011 2.784.058 3.807.045.975.207 1.504.344 1.857.182.466.399.8.748 1.15.35.35.683.566 1.15.748.353.137.882.3 1.857.344 1.054.048 1.37.058 4.041.058h.08c2.597 0 2.917-.01 3.96-.058.976-.045 1.505-.207 1.858-.344.466-.182.8-.398 1.15-.748.35-.35.566-.683.748-1.15.137-.353.3-.882.344-1.857.048-1.055.058-1.37.058-4.041v-.08c0-2.597-.01-2.917-.058-3.96-.045-.976-.207-1.505-.344-1.858a3.097 3.097 0 00-.748-1.15 3.098 3.098 0 00-1.15-.748c-.353-.137-.882-.3-1.857-.344-1.023-.047-1.351-.058-3.807-.058zM12 6.865a5.135 5.135 0 110 10.27 5.135 5.135 0 010-10.27zm0 1.802a3.333 3.333 0 100 6.666 3.333 3.333 0 000-6.666zm5.338-3.205a1.2 1.2 0 110 2.4 1.2 1.2 0 010-2.4z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </a>

                  <a
                    href="#"
                    class="rounded-full border border-gray-200 p-2 text-gray-900"
                  >
                    <span class="sr-only">Company Twitter</span>
                    <svg
                      class="h-4 w-4"
                      fill="currentColor"
                      viewBox="0 0 24 24"
                      aria-hidden="true"
                    >
                      <path
                        d="M8.29 20.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0022 5.92a8.19 8.19 0 01-2.357.646 4.118 4.118 0 001.804-2.27 8.224 8.224 0 01-2.605.996 4.107 4.107 0 00-6.993 3.743 11.65 11.65 0 01-8.457-4.287 4.106 4.106 0 001.27 5.477A4.072 4.072 0 012.8 9.713v.052a4.105 4.105 0 003.292 4.022 4.095 4.095 0 01-1.853.07 4.108 4.108 0 003.834 2.85A8.233 8.233 0 012 18.407a11.616 11.616 0 006.29 1.84"
                      />
                    </svg>
                  </a>
                </div>
              </div>
            </div>
          </div>

          <div class="p-6 bg-gray-100 mt-6 rounded-2xl">
            <h3 class="h3 text-gray-900 mb-4">Ünvan</h3>

            <iframe
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3172.3321820256856!2d-122.0135854237286!3d37.334643710437014!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x808fb596e9e188fd%3A0x3b0d8391510688f0!2sApple%20Park!5e0!3m2!1str!2saz!4v1717087176358!5m2!1str!2saz"
              class="w-full h-[200px]"
              allowfullscreen=""
              loading="lazy"
              referrerpolicy="no-referrer-when-downgrade"
            ></iframe>
          </div>
        </div>
      </div>
    </div>
  </div>
{/if}
