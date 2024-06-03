<script>
  import { TabGroup, Tab, TabAnchor } from "@skeletonlabs/skeleton";
  import { format } from "date-fns";
  import EmptyAvatarcon from "../../components/icons/EmptyAvatarİcon.svelte";
  import ProductCard from "../../components/ProductCard.svelte";
  let tabSet = 0;
</script>

<div class="custom-container mt-4">
  <div class="flex items-center gap-6 max-md:gap-3">
    <div
      class="w-28 h-28 max-md:w-20 max-md:h-20 max-sm:w-16 max-sm:h-16 bg-gray-300 rounded-full"
    >
      <div class=" w-full h-full flex items-center justify-center shrink-0">
        <EmptyAvatarcon />
      </div>
    </div>
    <div>
      <h2 class="h2">Username</h2>
      <div class="flex flex-col gap-[0.1rem] mt-[0.1rem]">
        <div class="text-gray-600 text-sm max-md:text-xs">
          Qatıldığı tarix:
          <span class="text-sm max-md:text-xs">
            {format(new Date(), "MMMM dd, yyyy")}
          </span>
        </div>
        <div class="text-gray-600 text-sm max-md:text-xs">
          Paylaşdığı elan sayı: <span class="text-sm max-md:text-xs"> 12 </span>
        </div>
      </div>
    </div>
  </div>
  <TabGroup class="mt-4">
    <Tab class="text-gray-800 " bind:group={tabSet} name="tab1" value={0}>
      <span>Aktiv</span>
    </Tab>
    <Tab class="text-gray-800" bind:group={tabSet} name="tab2" value={1}
      >Deaktiv olundu</Tab
    >
    <!-- Tab Panels --->
    <svelte:fragment slot="panel">
      {#if tabSet === 0}
        <ProductCard
          title={"item.title"}
          thumbnail={"item.thumbnail"}
          price={"item.price"}
          href="explore/{'item.id'}"
        />
      {:else if tabSet === 1}
        (tab panel 2 contents)
      {/if}
    </svelte:fragment>
  </TabGroup>
</div>
