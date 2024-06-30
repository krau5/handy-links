<script lang="ts" setup>
import { computed } from 'vue';
import links from '../assets/links.json';

type Props = {
  sortByCategory: string;
}

const props = defineProps<Props>();

const sortedLinks = computed(() => {
  if (props.sortByCategory === 'all') {
    return links;
  }

  return links.filter((link) => link.category === props.sortByCategory);
});
</script>

<template>
  <v-container
    fluid
    style="max-width: 1280px"
  >
    <v-row>
      <v-col
        v-for="link in sortedLinks"
        :key="link.name"
        cols="12"
        sm="4"
        md="3"
        class="d-flex"
      >
        <v-card
          :href="link.url"
          target="_blank"
          class="d-flex align-center justify-center text-center elevation-5 rounded-lg"
          style="width: 100%; height: 100px;"
        >
          <v-card-text class="text-body-1">
            {{ link.name }}
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
@media (hover: hover) {
  .v-card {
    transition: transform 0.2s;
  }

  .v-card:hover {
    transform: scale(1.05);
  }
}
</style>
