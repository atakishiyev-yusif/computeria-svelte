<script>
  import CategorieCard from "./CategorieCard.svelte";
</script>

<div
  class="bg-[#f3f3f3] p-6 flex gap-12 max-md:gap-2 max-lg:flex-col !overflow-scroll"
>
  <aside class="flex-1 bg-white p-6 rounded-lg">
    {#each Array(5) as item, index (index)}
      <div class="my-4 hover:text-purple-600">
        <a href="#">Link{index}</a>
      </div>
    {/each}
  </aside>
  <!-- <div
    class="w-3/4 max-lg:w-full grid grid-cols-4 h-[400px] max-sm:h-[250px] grid-rows-2 gap-6 max-md:gap-3"
  >
    <div class="col-span-2 row-span-2 max-md:row-span-1 bg-black relative">
      <CategorieCard
        title="Computers"
        description=" Black and White version of the PS5 coming out on sale."
        image="https://binternet.ahwx.org/image_proxy.php?url=https://i.pinimg.com/originals/a7/0f/dd/a70fdd1ded2ff21a01108026248e4c53.jpg"
      />
    </div>
    <div class="bg-black col-span-2 h-full relative">
      <CategorieCard
        title="Gaming"
        description="Black and White version of the PS5 coming out on sale.Black and White
            version of the PS5 coming out on sale."
        image="https://binternet.ahwx.org/image_proxy.php?url=https://i.pinimg.com/originals/a7/0f/dd/a70fdd1ded2ff21a01108026248e4c53.jpg"
      />
    </div>
    <div class="bg-black relative max-md:col-span-2">
      <CategorieCard
        title="Headphones"
        description="Headphones"
        image="https://binternet.ahwx.org/image_proxy.php?url=https://i.pinimg.com/originals/79/99/00/799900e8a82b6b94d26ad9b940cdbaff.jpg"
      />
    </div>
    <div class="bg-black relative max-md:col-span-2">
      <CategorieCard
        title="Accesories and more"
        description="Lorem ipsum dolor amet"
        image="https://binternet.ahwx.org/image_proxy.php?url=https://i.pinimg.com/originals/e0/55/32/e055326dcc4425f5900a7157abf3dd70.jpg"
      />
    </div>
  </div> -->
</div>
