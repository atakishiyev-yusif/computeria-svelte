<script>
  import { page } from "$app/stores";
  import ExploreIcon from "./icons/ExploreIcon.svelte";
  import HeartIcon from "./icons/HeartIcon.svelte";
</script>

<!-- component -->
<div
  class="fixed bottom-0 left-0 z-50 w-full h-16 bg-white border-t border-gray-200 dark:bg-gray-700 dark:border-gray-600"
>
  <div class="grid h-full max-w-lg grid-cols-4 mx-auto font-medium">
    <a
      href="/"
      type="button"
      class:active={$page.url.pathname === "/"}
      class="inline-flex flex-col items-center justify-center px-5 hover:bg-gray-50 dark:hover:bg-gray-800 group"
    >
      <svg
        class="w-6 h-6 mb-1 text-gray-500 dark:text-gray-400"
        fill="currentColor"
        viewBox="0 0 20 20"
        xmlns="http://www.w3.org/2000/svg"
        aria-hidden="true"
      >
        <path
          d="M10.707 2.293a1 1 0 00-1.414 0l-7 7a1 1 0 001.414 1.414L4 10.414V17a1 1 0 001 1h2a1 1 0 001-1v-2a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 001 1h2a1 1 0 001-1v-6.586l.293.293a1 1 0 001.414-1.414l-7-7z"
        ></path>
      </svg>
      <span class="text-xs whitespace-nowrap text-gray-500 dark:text-gray-400"
        >Əsas səhifə</span
      >
    </a>
    <a
      href="/explore"
      type="button"
      class:active={$page.url.pathname === "/explore"}
      class="inline-flex flex-col items-center justify-center px-5 hover:bg-gray-50 dark:hover:bg-gray-800 group"
    >
      <span class="text-gray-500 dark:text-gray-400">
        <ExploreIcon />
      </span>
      <span class="text-xs text-gray-500 dark:text-gray-400">Explore</span>
    </a>

    <a
      href="/favorites"
      type="button"
      class:active={$page.url.pathname === "/favorites"}
      class="inline-flex flex-col items-center justify-center px-5 hover:bg-gray-50 dark:hover:bg-gray-800 group"
    >
      <span class="text-gray-500 dark:text-gray-400">
        <HeartIcon />
      </span>
      <span class="text-xs text-gray-500 dark:text-gray-400">Favorilər</span>
    </a>

    <a
      href="/profile"
      type="button"
      class:active={$page.url.pathname === "/profile"}
      class="inline-flex flex-col items-center justify-center px-5 hover:bg-gray-50 dark:hover:bg-gray-800 group"
    >
      <svg
        class="w-6 h-6 mb-1 text-gray-500 dark:text-gray-400"
        fill="currentColor"
        viewBox="0 0 20 20"
        xmlns="http://www.w3.org/2000/svg"
        aria-hidden="true"
      >
        <path
          clip-rule="evenodd"
          fill-rule="evenodd"
          d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-6-3a2 2 0 11-4 0 2 2 0 014 0zm-2 4a5 5 0 00-4.546 2.916A5.986 5.986 0 0010 16a5.986 5.986 0 004.546-2.084A5 5 0 0010 11z"
        ></path>
      </svg>
      <span class="text-xs text-gray-500 dark:text-gray-400">Profil</span>
    </a>
  </div>
</div>

<style>
  .active * {
    color: var(--primary-color);
  }
</style>
