<template>
  <div class="formWrapper">
    <form @submit.prevent="handleSubmit">
      <label for="name">Name</label>
      <input
        type="text"
        id="name"
        name="name"
        placeholder="Name..."
        :value="cardData.name"
        disabled
      />

      <label for="value">Value</label>
      <input
        type="text"
        id="value"
        name="value"
        placeholder="Value..."
        :value="cardData.value"
        :disabled="!cardData.value"
      />

      <button type="submit" :disabled="!cardData.value">Edit</button>
    </form>
  </div>
</template>
<script>
export default {
  name: 'FormEditor',
  emits: ['editData'],
  props: {
    cardData: Object,
  },

  methods: {
    handleSubmit(event) {
      const editedData = {
        ...this.cardData,
        value: event.target[1].value || this.cardData.value,
      };
      this.$emit('editData', editedData);
    },
  },
};
</script>
<style lang="scss" scoped>
.formWrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px 0 80px;
}

form {
  max-width: 800px;
}

input[type='text'] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 7px;
  box-sizing: border-box;

  &:disabled {
    cursor: not-allowed;
  }

  &:focus-visible {
    outline: none;
  }
}

button {
  width: 100%;
  background-color: #3766ac;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 7px;
  transition: all 0.3s linear;
  cursor: pointer;

  &:hover:not([disabled]) {
    background-color: #2f499e;
  }

  &:disabled {
    cursor: not-allowed;
    opacity: 0.7;
  }
}
</style>
