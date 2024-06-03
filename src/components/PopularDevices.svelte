<script>
  import PopularDevicesCard from "./PopularDevicesCard.svelte";
  import SectionHeader from "./SectionHeader.svelte";
</script>

<section id="popular-devices" class="load-hidden mt-32">
  <SectionHeader title="Populyar cihazlar" description="Lorem ipsum dolor" />
  <div
    class="grid grid-rows-2 grid-cols-4 gap-6 max-sm:gap-3 mt-6 h-[800px] max-sm:h-[600px]"
  >
    <a
      href=""
      class="md:col-span-2 col-span-4 bg-white p-6 max-sm:p-3 hover:shadow-xl shadow-black flex flex-col"
    >
      <PopularDevicesCard
        title="IPS LCD Gaming Monitor"
        description="Lorem ipsum dolor amet"
        image="image"
      />
    </a>
    <a
      href=""
      class="col-span-2 bg-white md:p-6 p-3 hover:shadow-xl shadow-black"
    >
      <PopularDevicesCard
        title="AK-900 Wired Keyboard"
        description="Lorem ipsum dolor amet"
        image="image"
      />
    </a>
    <a
      href=""
      class="max-md:col-span-2 bg-white md:p-6 p-3 hover:shadow-xl shadow-black"
    >
      <PopularDevicesCard
        title="MacBook"
        description="All of the buttons, all of the savings"
        image="https://binternet.ahwx.org/image_proxy.php?url=https://i.pinimg.com/originals/4e/5f/cf/4e5fcf0005d423f45037171ab8574711.jpg"
      />
    </a>
    <a
      href=""
      class="bg-white md:p-6 p-3 col-span-2 hover:shadow-xl shadow-black"
    >
      <PopularDevicesCard
        title="Gaming consoles"
        description="From A to X"
        image="image"
      />
    </a>
    <a
      href=""
      class="bg-white md:p-6 p-3 max-md:col-span-2 hover:shadow-xl shadow-black transition-all"
    >
      <PopularDevicesCard
        title="MacBook"
        description="All of the buttons, all of the savings"
        image="https://binternet.ahwx.org/image_proxy.php?url=https://i.pinimg.com/originals/4e/5f/cf/4e5fcf0005d423f45037171ab8574711.jpg"
      />
    </a>
  </div>
</section>
