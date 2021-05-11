<template>
  <header>
      <div class="left-section">
          <img src="@/assets/img/boolflix.png" alt="Boolflix Logo">
      </div>

      <div class="right-section">
          <input
          type="text"
          placeholder="Search"
          v-model="getMovie">

          <button
          @click.prevent="$emit('getMovie', getMovie)">
          <i class="fas fa-search"></i></button>
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data(){
        return{
            getMovie: '',
        }
    }
}
</script>

<style scoped lang="scss">

@import '../styles/vars';

header {
    display: flex;
    justify-content: space-between;
    height: 80px;
    width: 100%;
    background-color: $black-a;
    position: fixed;
    z-index: 1;
}


.left-section {
    width: 170px;
    margin: 10px;
}


.left-section img {
    vertical-align: middle;
}


.right-section {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin:30px 70px;
}


.right-section input {
    margin-right: 10px;
    min-width: 96%;
    height: 30px;
    font-size: 12px;
    border-radius: 5px;
    border: 0;
    outline: none;
}


input:hover,
input:focus {
    border: 1px solid $red;
}


button {
    padding: 15px 10px;
    border-radius: 2px;
    background-color: $red;
    color: $white;
    cursor: pointer;
    position: relative;
}


button i {
    position: absolute;
    top: 8px;
    left: 3px;
}

</style>