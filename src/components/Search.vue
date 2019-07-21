<template>
  <div class="search">
    <input  class="search_input" type="search"
            v-on:keyup.enter="search"
            @input="search" v-model="content"
            placeholder="Search transaction">
    <button class="search_button" @click.enter="search">
      <i class="fas fa-search"></i>
    </button>
  </div>
</template>

<script>
export default {
  name: "Search",
  prop: ['value'],
  data:{
    return() {
      content: this.value
    }
  },
  methods: {
    search(e) {
      this.$emit("input", this.content)
    }
  }
}
</script>

<style lang="scss">
  .search {
    position: relative;
    padding: 8px 16px;
    background: #F0F1F4;
    opacity: 0.8;
    border-radius: 6px;
    margin: 25px 0;

    &_input {
      all: initial;
      appearance: none;
      width: 90%;
      color: $c-gray;
      font-size: 1.2rem;
      font-family: 'Sarabun', sans-serif;

      &::placeholder {
        font-size: 1.2rem;
        line-height: 18px;
        color: $c-gray;
        font-family: 'Sarabun', sans-serif;
      }
    }

    &_button {
      all: initial;
      appearance: none;
      position: absolute;
      top: 12px;
      right: 16px;
      font-size: 1.2rem;
      color: $c-gray;
    }
  }
</style>
