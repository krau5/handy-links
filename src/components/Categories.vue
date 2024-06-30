<script lang="ts" setup>
import { ref } from 'vue';

type Props = {
  categories: string[];
  selectedCategory: string;
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
    bg-color="primary"
  >
    <v-tab
      v-for="category in categories"
      :key="category"
      :value="category"
      style="outline: none; box-shadow: none !important"
      optional
      @click="handleCategoryClick(category)"
    >
      {{ formatCategoryName(category) }}
    </v-tab>
  </v-tabs>
</template>
