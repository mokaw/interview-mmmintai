<script setup lang="ts">
import { processItems } from '@/data/process-data';
import { ref } from 'vue'

const items = processItems;
/**
 * TODO: Disable this when challenge completed
 */
const isDebug = ref(true)
</script>

<template>
  <v-row>

    <v-col v-if="isDebug">

      <v-timeline side="end">

        <v-timeline-item v-for="(item, i) in items" :size="i !== items.length - 1 ? 'small' : 'large'"
          :dot-color="i !== items.length - 1 ? 'grey-lighten-1' : 'rgba(7, 133, 186, 0.824)'">

          <pre class="date">
            {{ item.timestamp.slice(11, 16) }} Uhr, {{ item.timestamp.slice(8, 10) }}.{{ item.timestamp.slice(5, 7) }}.{{ item.timestamp.slice(0, 4) }} 
          </pre>

          <v-alert rounded="xl" class="border-md process-card" v-if="i !== items.length - 1">
            <div class="d-flex justify-space-between">
              <div class="ma-4 title">{{ item.title }}</div>
              <div class="rounded-xl ma-2 pa-2 status">{{ item.status }}</div>
            </div>
            <div class=" ma-4 text-body-2 contact">
              Kontakt: {{ item.contact }}
            </div>
            <div class="comment"><v-icon class="ma-4" size="20">mdi-information</v-icon><span>{{ item.comment }}</span>
            </div>

          </v-alert>

          <v-alert rounded="xl" width="900px" max-width="100%" class="border-xl highlight"
            v-if="i === items.length - 1">
            <div class="d-flex justify-space-between">
              <div class="font-weight-black text-h5 ma-2">{{ item.title }}</div>
              <div class="rounded-xl ma-2 pa-2  highlight-status">{{ item.status }}</div>
            </div>
            <div class="font-weight-light ma-4 text-body-2">
              Kontakt: {{ item.contact }}
            </div>

            <div class="border-sm rounded-lg highlight-comment"><v-icon class="ma-4"
                size="20">mdi-information</v-icon><span>{{ item.comment }}</span></div>

          </v-alert>
        </v-timeline-item>
      </v-timeline>

    </v-col>
  </v-row>
</template>

<style scoped>
.date {
  font-family: sans-serif;
  padding-bottom: 15px;
  padding-left: 20px;
  color: rgba(36, 36, 36, 0.815);
}

.process-card {
  width: 800px;
  max-width: 100%;
  background-color: white;
  font-family: system-ui;
}

.title {
  font-weight: bold;
  font-size: large;
  color: rgba(36, 36, 36, 0.815);
}

.status {
  background-color: rgba(7, 133, 186, 0.824);
  ;
  color: aliceblue;
  font-weight: 600;
  width: 120px;
  text-align: center;
}

.contact {
  color: rgba(36, 36, 36, 0.45);
  font-weight: lighter;
}

.comment {
  color: aliceblue;
  background-color: rgba(7, 133, 186, 0.824);
  border: hidden;
  border-radius: 10px;
}

.highlight {
  background-color: rgba(7, 133, 186, 0.824);
  color: aliceblue;
  font-family: system-ui;
  font-size: large;
  font-weight: bolder;
}

.highlight-status {
  color: rgba(7, 133, 186, 0.824);
  background-color: aliceblue;
  font-weight: 600;
  width: 120px;
  text-align: center;
}

.highlight-comment {
  background-color: aliceblue;
  color: rgba(7, 133, 186, 0.824);
  border: hidden;
  border-radius: 10px;
  font-weight: 500;
}
</style>