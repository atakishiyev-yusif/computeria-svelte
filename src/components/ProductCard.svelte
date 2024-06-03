<script>
  export let title = "asdasfd";
  export let price = "asd";
  export let href = "Asfasd";
  export let isNew = false;
  export let thumbnail = "agasdas";
  export let isStore = false;
</script>

<a
  {href}
  class="product-card group relative block overflow-hidden flex-shrink-0"
>
  <button
    class="absolute end-4 top-4 z-10 rounded-full bg-white p-1.5 text-gray-900 transition hover:text-gray-900/75"
  >
    <span class="sr-only">Wishlist</span>

    <svg
      xmlns="http://www.w3.org/2000/svg"
      fill="none"
      viewBox="0 0 24 24"
      stroke-width="1.5"
      stroke="currentColor"
      class="h-4 w-4"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        d="M21 8.25c0-2.485-2.099-4.5-4.688-4.5-1.935 0-3.597 1.126-4.312 2.733-.715-1.607-2.377-2.733-4.313-2.733C5.1 3.75 3 5.765 3 8.25c0 7.22 9 12 9 12s9-4.78 9-12z"
      />
    </svg>
  </button>

  <img
    src={thumbnail}
    alt=""
    class="h-36 w-full object-cover transition duration-500 group-hover:scale-105 sm:h-64"
  />

  <div class="relative border border-gray-100 bg-white p-6 max-md:p-4">
    {#if isNew}
      <span
        class="whitespace-nowrap bg-[var(--primary-color)] text-white px-3 py-1.5 text-xs font-medium"
      >
        New
      </span>
    {/if}

    <h4 class="h4 font-medium text-gray-900 line-clamp-1">
      {title}
    </h4>

    <p class=" text-gray-700 h4">
      ₼
      <span>{price}</span>
    </p>
    <div class="mt-2 flex justify-between">
      <div class="flex items-center gap-1">
        <div class="w-6 h-6 overflow-hidden rounded-full bg-gray-500">
          <img src="" alt="" class="w-full h-full object-cover object-center" />
        </div>
        <div>
          <p>rwar</p>
        </div>
      </div>
      {#if isStore}
        <div>
          <a
            href="test"
            class="bg-[--primary-color-transparent] text-[--primary-color] font-bold rounded-3xl text-sm py-1 px-2"
          >
            Magaza
          </a>
        </div>
      {/if}
    </div>
  </div>
</a>

<style>
  .product-card {
    width: calc(25% - 12px);

    @media (min-width: 1536px) {
      width: calc(20% - 12px);
    }

    @media (max-width: 1024px) {
      width: calc(33.333333% - 12px);
    }

    @media (max-width: 640px) {
      width: calc(50% - 12px);
    }
  }
</style>
