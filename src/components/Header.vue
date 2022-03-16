<template>

  <header class="input">
    <h1 class="title">Boolflix</h1>
    <div>
      <input type="text" v-model="search" placeholder="Cerca film...">
      <button @click="$emit('search', search)">Cerca</button>
    </div>
  </header>

</template>

<script>

export default {
  name: 'MainHeader',
  data() {
    return {
      search: ''
    }
  }
  
}

</script>

<style scoped lang="scss">

.input {
  background-color: black;
  display: flex;
  gap: 15px;
  justify-content: space-between;
  padding: 20px 30px;
  align-items: center;
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 999;

  .title {
    text-transform: uppercase;
    color: red;
  }

  input {
    padding: 5px 15px;
    border-radius: 8px;
  }

  button {
    margin-left: 20px;
    padding: 5px 15px;
    border: none;
    background-color: red;
    color: white;
    border-radius: 8px;
    cursor: pointer;
  }

}

</style>
