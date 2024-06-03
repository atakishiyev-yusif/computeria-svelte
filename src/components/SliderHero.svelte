<script>
  import { onMount } from "svelte";

  const arry = [
    {
      id: 1,
      image: "https://picsum.photos/seed/picsum/1024/500",
    },
    {
      id: 2,
      image: "https://picsum.photos/id/870/1024/500?grayscale&blur=2",
    },
  ];

  let count = 0;
  let activeItem = null;

  $: onMount(() => {
    setInterval(() => {
      if (count !== arry.length) {
        activeItem = arry[count];
        count += 1;
      } else if (count === arry.length) {
        count = 0;
      }
    }, 2000);
  });
</script>

<div class="flex-[3]">
  {#if activeItem}
    <!-- svelte-ignore a11y-img-redundant-alt -->
    <div class="max-w-full w-full min-h-[70vh] max-md:min-h-[32vh]">
      <img src={activeItem.image} alt="image" loading="lazy" />
    </div>
  {:else}
    <div
      class="max-w-full w-full min-h-[70vh] max-md:min-h-[32vh] bg-gray-300 placeholder"
    ></div>
  {/if}
</div>
