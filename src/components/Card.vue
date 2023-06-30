<template>
  <div class="card">
    <article>
      <h3>{{ cardInfo.name }}</h3>
      <p>{{ cardInfo.value }}</p>
    </article>
    <button @click="$emit('handleEdit', cardInfo)">Edit</button>
  </div>
</template>
<script>
export default {
  name: 'CardItem',
  emits: ['handleEdit'],
  props: {
    cardInfo: Object,
  },
};
</script>
<style lang="scss" scoped>
.card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: max(100px, 147px);
  min-width: 150px;
  max-width: 250px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: all 0.3s linear;
  padding: 20px;
  border-radius: 10px;

  &:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  }

  h3 {
    color: #4a5372;
    font-size: 18px;
    font-weight: 600;
    margin-bottom: 15px;
  }

  p {
    color: #3e4766;
    margin-bottom: 15px;
    max-width: 110px;
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow: hidden;
  }

  button {
    width: 100%;
    background-color: #3766ac;
    border: none;
    border-radius: 10px;
    color: white;
    padding: 10px 20px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    cursor: pointer;
    transition: all 0.3s linear;

    &:hover {
      background-color: #2f499e;
    }
  }
}
</style>
