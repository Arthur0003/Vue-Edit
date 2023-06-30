<template>
  <h1 class="title">Cards</h1>
  <div class="cardsBlock">
    <CardItem
      v-for="card in cardsData"
      :key="card.name"
      :cardInfo="card"
      @handle-edit="handleEdit"
    />
  </div>
</template>

<script>
import CardItem from './Card.vue';

export default {
  name: 'CardsWrapper',
  emits: ['handleEdit'],
  props: {
    cardsData: Array,
  },
  components: {
    CardItem,
  },

  data() {
    return {};
  },
  methods: {
    handleEdit(card) {
      this.$emit('handleEdit', card);
    },
  },
};
</script>
<style lang="scss" scoped>
.title {
  margin-bottom: 50px;
  text-align: center;
}
.cardsBlock {
  display: flex;
  align-items: center;
  justify-content: center;
  column-gap: 50px;
}
</style>
