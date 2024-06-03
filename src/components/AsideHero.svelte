<aside class="flex-1 bg-white p-6 rounded-lg max-md:hidden">
  {#each Array(5) as item, index (index)}
    <div class="my-4 hover:text-purple-600">
      <a href="#">Link{index}</a>
    </div>
  {/each}
</aside>
