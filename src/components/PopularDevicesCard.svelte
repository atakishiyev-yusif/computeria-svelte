<script>
  export let title, description, image;
</script>

<div class="h-[80%] flex items-center justify-center">
  <img src={image} class="max-w-full max-h-full object-cover" />
</div>

<h4
  class="h4 max-sm:text-sm"
  style="display: -webkit-box; -webkit-box-orient:vertical; -webkit-line-clamp:1; overflow:hidden"
>
  {title}
</h4>
<p
  class="text-gray-500 max-sm:text-xs"
  style="display: -webkit-box; -webkit-box-orient:vertical; -webkit-line-clamp:1; overflow:hidden"
>
  {description}
</p>
