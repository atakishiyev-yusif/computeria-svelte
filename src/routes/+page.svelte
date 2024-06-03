<script>
  import axios from "axios";

  import Categories from "../components/Categories.svelte";
  import Footer from "../components/Footer.svelte";
  import Hero from "../components/Hero.svelte";
  import MostWanted from "../components/MostWanted.svelte";
  import PopularDevices from "../components/PopularDevices.svelte";
</script>

<div>
  <div class="custom-container mt-2">
    <Hero />
    <MostWanted />
    <PopularDevices />
    <Categories />
  </div>
</div>
