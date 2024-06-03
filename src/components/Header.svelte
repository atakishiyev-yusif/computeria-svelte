<script>
  import { initializeStores, Drawer } from "@skeletonlabs/skeleton";
  import { getDrawerStore } from "@skeletonlabs/skeleton";
  import Logo from "./Logo.svelte";
  import SearchBar from "./SearchBar.svelte";
  import CloseIcon from "./icons/CloseIcon.svelte";

  initializeStores();

  const drawerStore = getDrawerStore();

  const headerLinks = [
    {
      id: "home",
      title: "Əsas səhifə",
      href: "/",
    },
    {
      id: "explore",
      title: "Kəşf et",
      href: "/explore",
    },
    {
      id: "contact",
      title: "Əlaqə",
      href: "/contact",
    },
    {
      id: "about",
      title: "Haqqımızda",
      href: "/about",
    },
  ];
</script>

<header
  class="max-md:hidden border-b py-4 max-md:py-2 max-md:sticky max-md:top-0 max-md:z-40 backdrop-blur-xl bg-white"
>
  <div class="custom-container flex items-center justify-between">
    <Logo />
    <nav class="flex items-center gap-5 max-md:hidden">
      {#each headerLinks as link, i (link.id)}
        <a href={link.href}>{link.title}</a>
      {/each}
    </nav>
    <div class="flex items-center gap-2">
      <a href="/login" class="btn variant-filled px-8 login-button">Daxil ol</a>
    </div>
  </div>
</header>

<div class="sticky top-0 z-[999] searchbar">
  <SearchBar />
</div>
