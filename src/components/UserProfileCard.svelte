<script>
  export let imageSrc, name, mail;
</script>

<div class="flex items-center gap-4">
  <div class="w-16 h-16 rounded-full bg-gray-400 flex-shrink-0">
    <img
      src={imageSrc}
      alt={`${name} profile`}
      class="w-full h-full object-cover"
    />
  </div>
  <div>
    <h3 class="h3">{name}</h3>
    <p class="text-gray-400">{mail}</p>
  </div>
</div>
