<script>
  export let title, description, image;
</script>

<img src={image} class="w-full h-full opacity-80 object-cover" />
<div class="absolute bottom-0 md:p-8 p-4 text-white">
  <h4
    class="h4 max-sm:text-sm"
    style="display: -webkit-box; -webkit-box-orient:vertical; -webkit-line-clamp:1; overflow:hidden"
  >
    {title}
  </h4>
  <p
    class=" max-sm:text-xs my-2 max-sm:my-1"
    style="display: -webkit-box; -webkit-box-orient:vertical; -webkit-line-clamp:1; overflow:hidden"
  >
    {description}
  </p>
  <a
    href=""
    class="max-sm:text-sm font-medium border-b-2 border-[#868686] hover:opacity-70"
    >Shop now</a
  >
</div>
