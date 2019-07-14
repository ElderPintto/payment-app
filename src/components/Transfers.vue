<template>
  <div class="transfers">
    <template>  <!-- template foi usando para n colcoar nenhuma tag especifica sendo pai dos itens -->
      <Trasnfer class="transfers_item" v-for="trasnfer in transfers" :key="trasnfer.id" :trasnfer=trasnfer>
      </Trasnfer>
    </template>
  </div>
</template>

<script>
import Trasnfer from "@/components/Trasnfer.vue";

export default {
  name: "transfers",
  components: {
    Trasnfer
  },
  props: {
    transfers: {
      type: Array,
      required: true
    }
  },
  methods: {

  }
}
</script>

<style lang="scss">
  .transfers {
    padding-top: 10px;
    padding-bottom: 100px;
    overflow: auto;
    max-height: 300px;
    &_item {
      padding: 14px;
      margin-bottom: 16px;

      figure {
        margin-right: 10px;
      }

      .transfer_date {
        color: $c-black-gray;
      }
    }
  }
</style>
