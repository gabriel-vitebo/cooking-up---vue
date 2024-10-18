<script lang="ts">
import {fetchCategories} from "@/http";
import type ICategories from "@/interfaces/ICategories";
import CardCategory from "@/components/CardCategory.vue";
import MainButton from "@/components/MainButton.vue";

export default {
  components: {MainButton, CardCategory},
  data() {
    return {
      categories: [] as ICategories[]
    }
  },
  async created() {
    this.categories = await fetchCategories();
  },
  emits: ["addIngredient", "removeIngredient"],
}
</script>

<template>
  <section class="selectIngredients">
    <h1 class="header ingredientsTitle">Ingredientes</h1>

    <p class="paragraph-lg instructions">
      Selecione abaixo os ingredientes que você quer usar nessa receita:
    </p>

    <ul class="category">
      <li v-for="category in categories" :key="category.name">
        <CardCategory
            :category="category"
            @add-ingredient="$emit('addIngredient', $event)"
            @remove-ingredient="$emit('removeIngredient', $event)"
        />
      </li>
    </ul>

    <p class="paragraph tip">
      *Atenção: consideramos que você tem em casa sal, pimenta e água.
    </p>
    <MainButton text="Buscar Receitas!" />

  </section>
</template>

<style scoped>
.selectIngredients {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.ingredientsTitle {
  color: var(--verde-medio, #3D6D4A);
  display: block;
  margin-bottom: 1.5rem;
}

.instructions {
  margin-bottom: 2rem;
}

.category {
  margin-bottom: 1rem;
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.tip {
  align-self: flex-start;
  margin-bottom: 3.5rem;
}

@media only screen and (max-width: 767px) {
  .tip {
    margin-bottom: 2.5rem;
  }
}
</style>