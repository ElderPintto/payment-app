<template>
  <nav class="nav-menu">
    <ul class="nav-menu_list">
      <li class="nav-menu_item">
        <button>
          <i class="fas fa-home"></i>
        </button>
      </li>
      <li class="nav-menu_item">
        <button>
          <i class="fas fa-wallet"></i>
        </button>
      </li>
      <li class="nav-menu_item middle">
        <button>
          <i class="fas fa-camera"></i>
        </button>
      </li>
      <li class="nav-menu_item">
        <button>
          <i class="fas fa-chart-pie"></i>
        </button>
      </li>
      <li class="nav-menu_item">
        <button>
          <i class="fas fa-cog"></i>
        </button>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "menuu",
}
</script>

<style lang="scss">
  .nav-menu {
    position: fixed;
    width: 100%;
    bottom: 0;
    left: 0;
    background: $c-white;
    padding: 10px 0 15px;
    box-shadow: 0px -4px 14px rgba(0, 0, 0, 0.06);

    &:after {
      content: "";
      position: absolute;
      bottom: 8px;
      display: block;
      width: 35%;

      height: 5px;
      left: 50%;
      border-radius: 3px;
      border-bottom: 5px solid #D6D9E4;;
      transform: translate(-50%, -50%);
    }

    &_list {
      display: flex;
      list-style: none;
      justify-content: space-around;
      padding: 0;
    }
    &_item {
      width: 100%;
      position: relative;
      text-align: center;

      button {
        appearance: none;
        background: none;
        border: none;
        font-size: 25px;
        color: #A6AAB4;
      }

      &.active {
        background: #613EEA;
      }

      &.middle {
        transform: translateY(-50px);
        button {
          width: 55px;
          height: 55px;
          border-radius: 100%;
          background: #613EEA;
          color: $c-white;
          box-shadow: 0px 4px 12px rgba(97, 62, 234, 0.5);
        }
      }
    }
  }
</style>
