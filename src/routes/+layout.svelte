<script>
  import "../app.postcss";

  // Floating UI for Popups
  import {
    computePosition,
    autoUpdate,
    flip,
    shift,
    offset,
    arrow,
  } from "@floating-ui/dom";
  import { storePopup } from "@skeletonlabs/skeleton";
  import Header from "../components/Header.svelte";
  import Footer from "../components/Footer.svelte";
  import SearchBar from "../components/SearchBar.svelte";
  import BottomNav from "../components/BottomNav.svelte";
  storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });

  // searchbar true oldugunda gorunsun false oldugunda gorunmesin
  // searchbar = false
  // writable
</script>

<Header />
<div class="md:hidden">
  <BottomNav />
</div>
<main>
  <slot />
</main>
<Footer />

<style>
  :global(*) {
    font-size: 16px;
  }

  :global(html, body) {
    background: #f3f3f3 !important;
  }

  :global(main) {
    min-height: 100vh;
  }
</style>
