<script setup lang="ts">
import type { GalleryItem } from '@/lib/gallery-item.d.ts'

const props = defineProps({ item: Array as () => GalleryItem[] })


</script>

<template>
  <vue-picture-swipe
    class="my-gallery"
    :items="props.item"
    :options="{ shareEl: false, rotationOn: true }"
  ></vue-picture-swipe>
</template>

<style scoped>
::v-deep .my-gallery img {
  max-width: 300px;
  height: auto;
  display: block;
  margin: 0 auto;
}
</style>
