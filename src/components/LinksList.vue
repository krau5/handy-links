<script lang="ts" setup>
import links from '../assets/links.json';
</script>

<template>
  <div>
    <v-container fluid>
      <v-row>
        <v-col
          v-for="link in links"
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
            <v-card-text class="text-body-1">{{ link.name }}</v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<style scoped>
.v-card {
  transition: transform 0.2s;
}
.v-card:hover {
  transform: scale(1.05);
}
</style>


