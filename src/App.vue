<script lang="ts" setup>
import { ref } from "vue";
import LinksList from './components/LinksList.vue';
import Categories from './components/Categories.vue';
import Cover from './components/Cover.vue';

const categories = ['learning', 'repo', 'article']

const category = ref<string | null>(null)

const handleClick = (newCategory: string) => {
  if (category.value === newCategory) {
    category.value = null;
    return;
  }

  category.value = newCategory;
};
</script>

<template>
  <Cover>
    <h3 class="text-h3 font-weight-bold text-center mb-4">
      Handy Links
    </h3>

    <Categories
      :on-click="handleClick"
      :categories="categories"
      :selected-category="category"
    />
  </Cover>

  <LinksList :sort-by-category="category" />
</template>

