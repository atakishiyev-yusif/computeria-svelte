<script>
  import CategorieCard from "./CategorieCard.svelte";
  import SectionHeader from "./SectionHeader.svelte";
</script>

<section id="categories" class="my-32">
  <SectionHeader title="Kateqoriyalar" description="Lorem ipsum dolor " />

  <div
    class="grid grid-cols-4 h-[600px] max-sm:h-[250px] grid-rows-2 gap-6 max-sm:gap-3"
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
  </div>
</section>
