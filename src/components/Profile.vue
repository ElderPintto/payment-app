<template>
  <figure class="profilePhoto" :class="{profilePhoto__logged : status}">
    <span >
      <img class="profilePhoto_image" :src="require(`../assets/${img}`)" alt="teste">
    </span>
    <figcaption class="profilePhoto_status"></figcaption>
  </figure>
</template>

<script>
export default {
  name: "profileImage",
  props: ["img", "status"]
}
</script>

<style lang="scss">
  .profilePhoto {
    position: relative;
    width: 32px;
    height: 32px;

    &__logged {
      .profilePhoto_status {
        position: absolute;
        display: block;
        top: 0;
        right: -5px;
        width: 8px;
        height: 8px;
        z-index: 1;
        border: 2px solid $c-white;
        border-radius: 100%;
        background: $c-green-positive;
        box-sizing: content-box;
      }
    }

    &_image {
      border-radius: 50%;
      box-sizing: content-box;
      width: 100%;
      height: auto

    }
  }
</style>
