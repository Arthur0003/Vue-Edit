<template>
  <div class="mainWrapper">
    <Editor msg="Welcome to Your Vue.js App" />
    <Form :cardData="cardData" @edit-data="editData" />
    <Cards @handle-edit="handleEdit" :cardsData="cardsData" />
  </div>
</template>

<script>
import Editor from './components/EditorTitle.vue';
import Form from './components/Form.vue';
import Cards from './components/Cards.vue';

export default {
  name: 'App',
  components: {
    Editor,
    Form,
    Cards,
  },

  data() {
    return {
      cardsData: [
        {
          name: 'foo1',
          value: 'bar1',
        },
        {
          name: 'foo2',
          value: 'bar2',
        },
        {
          name: 'foo3',
          value: 'bar3',
        },
        {
          name: 'foo4',
          value: 'bar4',
        },
        {
          name: 'foo5',
          value: 'bar5',
        },
      ],
      cardData: {},
    };
  },

  methods: {
    handleEdit(card) {
      this.cardData = card;
    },
    editData(data) {
      this.cardsData = this.cardsData.map((card) => {
        if (card.name === data.name) {
          card.value = data.value;
        }
        return card;
      });
      this.cardData = {};
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  min-height: 100vh;
}

.mainWrapper {
  display: flex;
  flex-direction: column;
}
</style>
