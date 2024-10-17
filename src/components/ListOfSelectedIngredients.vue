<script lang="ts">
import Tag from "@/components/Tag.vue"

export default {
  name: 'YourList',
  components: {Tag},
  props: {
    ingredients: {type: Array as () => string[], required: true},
  }
}
</script>

<template>
  <section>
      <span class="subtitle-lg your-list-text">
        Sua lista:
      </span>
    <ul v-if="ingredients.length" class="ingredient-your-list">
      <li v-for="ingredient in ingredients" :key="ingredient">
        <Tag :text="ingredient" active/>
      </li>
    </ul>

    <p v-else class="paragraph empty-list">
      <img src="../assets/images/icones/lista-vazia.svg" alt="Ícone de pesquisa"/>
      Sua lista está vazia, selecione ingredientes para iniciar.
    </p>
  </section>
</template>
<style scoped>

.your-list-text {
  color: var(--coral, #F0633C);
  display: block;
  text-align: center;
  margin-bottom: 1.5rem;
}

.ingredient-your-list {
  display: flex;
  justify-content: center;
  gap: 1rem 1.5rem;
  flex-wrap: wrap;
}


.empty-list {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.25rem;

  color: var(--coral, #F0633C);
  text-align: center;
}

@media only screen and (max-width: 1300px) {
}

@media only screen and (max-width: 767px) {
}
</style>