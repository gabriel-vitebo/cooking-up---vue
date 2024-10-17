<script lang="ts">
  import type {PropType} from "vue";
  import type ICategories from "@/interfaces/ICategories";
  import Tag from "@/components/Tag.vue";
  import SelectableIngredient from "@/components/SelectableIngredient.vue";

  export default {
    components: {SelectableIngredient, Tag},
    props: {
      category: {type: Object as PropType<ICategories>, required: true},
    },
    emits: ['addIngredient']
  }
</script>

<template>
  <article class="category">
    <header class="header-category">
      <img :src="`/imagens/icones/categorias_ingredientes/${category.image}`" :alt="`Icone da categoria ${category.name}`" class="image-category">
      <h2 class="paragraph-lg name-category">{{category.name}}</h2>
    </header>
    <ul class="ingredients-category">
      <li v-for="ingredient in category.ingredients" :key="ingredient">
        <SelectableIngredient
            :ingredient="ingredient"
            @add-ingredient="$emit('addIngredient', $event)"
        />
      </li>
    </ul>
  </article>
</template>

<style scoped>
.category {
  width: 19.5rem;
  padding: 1rem;
  border-radius: 1rem;
  background: var(--branco, #FFF);
  box-shadow: 4px 4px 10px 0px rgba(68, 68, 68, 0.05);
  height: 100%;

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

.header-category {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.image-category {
  width: 3.5rem;
}

.name-category {
  text-align: center;
  color: var(--verde-medio, #3D6D4A);
  font-weight: 700;
}

.ingredients-category{
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  flex-wrap: wrap;
}
</style>