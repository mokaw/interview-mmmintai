<script setup lang="ts">
import DropField from '@/components/DropField.vue';
import ImageGallery from '@/components/ImageGallery.vue';
import type { GalleryItem } from '@/lib/gallery-item';
import { ref } from 'vue';

const galleryItem = ref<GalleryItem[]>([])

function loadFiles(files: any) {
  try{
    for (const file of files) {
      const newItem: GalleryItem = {
        src: URL.createObjectURL(file),
        thumbnail: URL.createObjectURL(file),
        w: 1200,
        h: 800,
        title: file.name,
      };
      galleryItem.value.push(newItem);
    }
    }catch(error){
      console.error(error, 'Fehler beim Laden der Dateien')
    }

}

</script>

<template>
  <v-row>
    <v-col cols="12">
      <DropField accept=".jpg, .jpeg, .png, .webp" @drop="loadFiles"></DropField>
      <ImageGallery :item = "galleryItem"></ImageGallery>
    </v-col>
  </v-row>
</template>
