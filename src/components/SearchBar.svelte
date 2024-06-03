<script>
  import CartIcon from "./icons/CartIcon.svelte";
  import GridIcon from "./icons/GridIcon.svelte";
  import HeartIcon from "./icons/HeartIcon.svelte";
  import CategoryMenu from "./CategoryMenu.svelte";

  let categoryMenu = false;

  const handleCategoryMenu = () => {
    categoryMenu = !categoryMenu;
    if (categoryMenu) {
      document.body.classList.add("overflow-hidden");
    } else {
      document.body.classList.remove("overflow-hidden");
    }
  };
</script>

<div class="shadow-sm shadow-[#E3D9E3] py-3 max-md:py-2 backdrop-blur-xl">
  <div class="flex items-center justify-between custom-container">
    <button on:click={handleCategoryMenu}>
      <GridIcon />
    </button>
    <div class="w-2/3 max-md:mx-auto">
      <input class="input" title="Axtarış" type="text" placeholder="Axtarış" />
    </div>
    <div class="flex items-center gap-6 max-md:hidden">
      <a href="/favorites" class="flex items-center gap-1">
        <HeartIcon />
        <span> Favorilər </span>
      </a>
    </div>
  </div>
</div>

<div
  class="transition-all duration-1000 -translate-y-24 {categoryMenu
    ? 'opacity-100 -translate-y-0 h-[100vh] w-full mt-24'
    : 'opacity-0 invisible h-0'}"
>
  <CategoryMenu />
</div>
