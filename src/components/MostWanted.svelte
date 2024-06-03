<script>
  import axios from "axios";
  import { onMount } from "svelte";
  import ProductCard from "./ProductCard.svelte";
  import SectionHeader from "./SectionHeader.svelte";

  let products = [];

  const getProducts = async () => {
    const response = await axios.get("https://dummyjson.com/products");
    products = response.data.products;
  };

  onMount(() => {
    getProducts();
  });
</script>

<section id="most-wanted" class="mt-32">
  <SectionHeader
    title="Ən çox axtarılan"
    description="Lorem ipsum dolor sit amet."
  />

  <div class="flex overflow-x-auto gap-3">
    {#each products as item (item.id)}
      <ProductCard
        title={item.title}
        thumbnail={item.thumbnail}
        price={item.price}
        href="explore/{item.id}"
      />
    {/each}
  </div>
</section>
