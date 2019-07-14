<template>
  <div class="selecttion-operation">
    <template>
      <button class="selecttion-operation_button"
        v-for="(operation, index) in operations"
        :key="index"
        :class="{active : operation.active}"
        @click="typeTranfers">
        {{operation.name}}
      </button>
    </template>
  </div>
</template>

<script>
export default {
  name: 'SelectionOperation',
  props: {
    operations: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      active: ''
    }
  },
  methods: {
    typeTranfers() {
      this.$emit('cliqueaqui')
    }
  }
}
</script>

<style lang="scss">
  .selecttion-operation {
    width: 100%;
    display: flex;
    flex-wrap: nowrap;
    border-bottom: 1px solid #E8E9EC;
    &_button {
      width: 100%;
      appearance: none;
      border: none;
      background: none;
      padding: 13px;

      font-weight: 600;
      font-size: 18px;
      line-height: 28px;
      letter-spacing: 0.1px;
      color:  #A6AAB4;


      &.active {
        color: #3B414B;
        position: relative;
        outline: none;
        &:after {
          content: "";
          position: absolute;
          bottom: -1px;
          display: block;
          width: 50%;
          height: 1px;
          left: 50%;
          border-radius: 3px;
          border-bottom: 1px solid red;
          transform: translate(-50%, -50%);
        }
      }
    }
  }
</style>
