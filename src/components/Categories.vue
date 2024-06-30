<script lang="ts" setup>
import { ref } from 'vue';

type Props = {
  categories: string[];
  selectedCategory: string | null;
  onClick: (category: string) => void;
}

const props = defineProps<Props>();

const selectedCategory = ref(props.selectedCategory);

const handleCategoryClick = (category: string) => {
  selectedCategory.value = category;

  props.onClick(category);
};

const formatCategoryName = (category: string) => {
  return category.charAt(0).toUpperCase() + category.slice(1);
};
</script>

<template>
  <v-tabs
    v-model="selectedCategory"
    bg-color="primary"
  >
    <v-tab
      v-for="category in categories"
      :key="category"
      :value="category"
      @click="handleCategoryClick(category)"
      style="outline: none; box-shadow: none !important"
    >
      {{ formatCategoryName(category) }}
    </v-tab>
  </v-tabs>
</template>
