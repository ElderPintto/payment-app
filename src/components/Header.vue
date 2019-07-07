<template>
  <header class="header container">
    <div class="header_row row">
      <div class="header_box header_title">
        <h3 class="header_subtitle title title_subtitle">Your balance</h3>
        <h1 class="header_title title title_page">$ 926.21</h1>
      </div>
      <div class="header_box header_profilePhoto">
        <Profile
        :img=imageUrlBase
        :status=statusProfile
        ></Profile>
      </div>
    </div>
  </header>
</template>

<script>

import Profile from "@/components/Profile.vue";

export default {
  name: "main-header",
  components: {
    Profile
  },
  data() {
    return {
      imageUrlBase : 'profile.jpg',
      statusProfile: true,
    }
  },
}
</script>

<style lang="scss">
  .header {

    &_row {
      align-items: flex-end;
      justify-content: space-between;
    }

    &_box {

    }

    &_profilePhoto {
      display: flex;
      justify-content: left;
    }
  }
</style>
