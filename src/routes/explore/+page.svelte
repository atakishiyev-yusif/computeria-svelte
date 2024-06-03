<script>
  import { onMount } from "svelte";
  import axios from "axios";

  import { Accordion, AccordionItem } from "@skeletonlabs/skeleton";
  import StoreIcon from "../../components/icons/StoreIcon.svelte";
  import StatusIcon from "../../components/icons/StatusIcon.svelte";
  import PiggyBankIcon from "../../components/icons/PiggyBankIcon.svelte";
  import ProductCard from "../../components/ProductCard.svelte";
  import FilterIcon from "../../components/FilterIcon.svelte";
  import PanelLeftCloseIcon from "../../components/icons/PanelLeftCloseIcon.svelte";

  let type;
  let status;
  let price;
  let minPrice;
  let maxPrice;

  let products = [];

  const getProducts = async () => {
    const response = await axios.get("https://dummyjson.com/products");
    products = response.data.products;
  };

  onMount(() => {
    getProducts();
  });

  let openMenu = false;

  $: if (openMenu) {
    document.body.style.overflowY = "hidden";
  } else {
    document.body.style.overflowY = "auto";
  }

  $: console.log("openMenu", openMenu);

  $: console.log("maxPrice : ", maxPrice);
  $: console.log("minPrice : ", minPrice);
</script>

<button
  type="button"
  class="text-gray-700 menu-button m-5 flex items-center gap-2"
  on:click={() => {
    openMenu = !openMenu;
  }}
>
  <span>
    <FilterIcon />
  </span>
  Filtrlər</button
>

<div
  on:click={() => {
    openMenu = !openMenu;
  }}
  class="absolute top-0 right-0 bottom-0 bg-black w-screen z-[999] bg-opacity-40 {openMenu
    ? 'block'
    : 'hidden'}"
></div>
<div class="flex">
  <div
    class="flex-1 px-5 rounded-xl transition-all duration-500 max-xl:z-30 max-xl:absolute max-xl:-left-full {openMenu &&
      'max-xl:left-0 max-xl:h-screen max-xl:z-[99999] max-xl:w-[50vh] max-md:w-[30vh] max-sm:w-[40vh]'} bg-white py-5"
  >
    <button
      on:click={() => {
        openMenu = !openMenu;
      }}
      class="-mt-1 mb-7 text-gray-500 menu-button"
      ><PanelLeftCloseIcon /></button
    >
    <div class="sticky top-20 mt-2">
      <Accordion class="flex flex-col gap-4">
        <AccordionItem open>
          <svelte:fragment slot="lead">
            <span class="text-[--primary-color]">
              <StoreIcon />
            </span>
          </svelte:fragment>
          <svelte:fragment slot="summary">
            <h3 class="text-gray-800">Type</h3>
          </svelte:fragment>
          <svelte:fragment slot="content">
            <div
              class="flex items-center ps-4 border border-gray-200 rounded dark:border-gray-700"
            >
              <input
                id="store"
                type="radio"
                name="store"
                on:change={(e) => {
                  type = e.currentTarget.id;
                }}
                class="w-4 h-4 text-[--primary-color] bg-gray-100 border-gray-300 focus:ring-[--primary-color] dark:focus:ring-[--primary-color] dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
              />
              <label
                for="store"
                class="w-full py-4 ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                >Mağaza</label
              >
            </div>
            <div
              class="flex items-center ps-4 border border-gray-200 rounded dark:border-gray-700"
            >
              <input
                id="user"
                type="radio"
                name="store"
                on:change={(e) => {
                  type = e.currentTarget.id;
                }}
                class="w-4 h-4 text-[--primary-color] bg-gray-100 border-gray-300 focus:ring-[--primary-color] dark:focus:ring-[--primary-color] dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
              />
              <label
                for="user"
                class="w-full py-4 ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                >User</label
              >
            </div>
          </svelte:fragment>
        </AccordionItem>
        <AccordionItem>
          <svelte:fragment slot="lead">
            <span class="text-[--primary-color]">
              <StatusIcon />
            </span>
          </svelte:fragment>
          <svelte:fragment slot="summary">
            <h3 class="text-gray-800">Vəziyyəti</h3>
          </svelte:fragment>
          <svelte:fragment slot="content">
            <div
              class="flex items-center ps-4 border border-gray-200 rounded dark:border-gray-700"
            >
              <input
                id="new"
                type="radio"
                name="new"
                on:change={(e) => {
                  type = e.currentTarget.id;
                }}
                class="w-4 h-4 text-[--primary-color] bg-gray-100 border-gray-300 focus:ring-[--primary-color] dark:focus:ring-[--primary-color] dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
              />
              <label
                for="new"
                class="w-full py-4 ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                >Yeni</label
              >
            </div>
            <div
              class="flex items-center ps-4 border border-gray-200 rounded dark:border-gray-700"
            >
              <input
                id="used"
                type="radio"
                name="new"
                on:change={(e) => {
                  type = e.currentTarget.id;
                }}
                class="w-4 h-4 text-[--primary-color] bg-gray-100 border-gray-300 focus:ring-[--primary-color] dark:focus:ring-[--primary-color] dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
              />
              <label
                for="used"
                class="w-full py-4 ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                >İstifadə olunmuş</label
              >
            </div>
          </svelte:fragment>
        </AccordionItem>
        <AccordionItem>
          <svelte:fragment slot="lead">
            <span class="text-[--primary-color]">
              <PiggyBankIcon />
            </span>
          </svelte:fragment>
          <svelte:fragment slot="summary">
            <h3 class="text-gray-800">Qiymət</h3>
          </svelte:fragment>
          <svelte:fragment slot="content">
            <div class="flex mt-2 gap-2">
              <input
                class="input h-10"
                title="Min. qiymət"
                bind:value={minPrice}
                type="number"
                placeholder="Min. qiymət"
              />
              <input
                class="input h-10"
                title="Maks. qiymət"
                bind:value={maxPrice}
                type="number"
                placeholder="Maks. qiymət"
              />
            </div>
          </svelte:fragment>
        </AccordionItem>
        <!-- ... -->
      </Accordion>

      <button
        type="button"
        class="btn variant-ringed w-full hover:variant-filled hover:bg-[--primary-color] mt-6"
        >Göstər</button
      >
    </div>
  </div>
  <div class="flex-[4] mx-2">
    <div class="flex flex-wrap items-start justify-center gap-[12px]">
      {#each products as item (item.id)}
        <ProductCard
          title={item.title}
          thumbnail={item.thumbnail}
          price={item.price}
          href="explore/{item.id}"
        />
      {/each}
    </div>
  </div>
</div>

<style>
  @media (min-width: 1280px) {
    .menu-button {
      display: none;
    }
  }
</style>
