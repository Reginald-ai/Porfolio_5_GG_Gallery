<template>
  <header>
    <div class="navbar">
      <div class="container">
        <NuxtLink to="/" class="navbar-brand">
          <img src="#" alt="" />
          GG-Gallery
        </NuxtLink>
        <button @click="navbar_btn" class="navbar-btn">
          <span></span>
        </button>
        <ul :class="{ opens: ifActive }" class="navbar-nav-dropdown">
          <li class="nav-item">
            <NuxtLink to="/About" class="nav-link">About</NuxtLink>
          </li>
          <li class="nav-item">
            <NuxtLink to="/Contact" class="nav-link">Contact</NuxtLink>
          </li>
        </ul>
        <ul class="navbar-nav">
          <li class="nav-item">
            <NuxtLink to="/About" class="nav-link">About</NuxtLink>
          </li>
          <li class="nav-item">
            <NuxtLink to="/Contact" class="nav-link">Contact</NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      ifActive: false,
    };
  },
  methods: {
    navbar_btn() {
      this.ifActive = !this.ifActive;
    },
  },
};
</script>

<style lang="scss">
.container {
  position: relative;
  // padding: 0;
}
.navbar {
  .navbar-brand {
    color: #333333;
  }
  .navbar-btn {
    height: 30px;
    outline: none;
    border: none;
    background: none;
    @include breakpoint-up(md) {
      display: none;
    }
    span,
    ::after,
    ::before {
      content: "";
      width: 30px;
      height: 3px;
      background: #000000;
      display: block;
    }

    span::after {
      transform: translateY(-11px);
    }
    span::before {
      transform: translateY(8px);
    }
  }
  .navbar-nav-dropdown {
    display: flex;
    margin: 0;
    flex-direction: column;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, 10%);
    background: #333333;
    width: 94%;
    padding: 20px;
    justify-content: center;
    z-index: 999;
    transition: all 0.6s ease;
    border-radius: 0px 0px 20px 20px;
    list-style-type: none;
    justify-content: center;
    align-items: center;
    opacity: 0;
    margin-top: -700px;
    &.opens {
      margin: 0;
      opacity: 1;
    }
    @include breakpoint-up(md) {
      display: none;
    }

    .nav-item {
      width: 100%;
      text-align: center;
      padding: 10px;
      -webkit-box-shadow: 0 3px 20px 0 rgb(0 0 0 / 30%);
      box-shadow: 0 3px 20px 0 rgb(0 0 0 / 30%);
      border-radius: 30px 30px 30px 0;
      margin-bottom: 10px;
      position: relative;
      .nav-link {
        color: #ffff;
        margin-bottom: 10px;
      }
    }
  }
  .navbar-nav {
    display: none;
    @include breakpoint-up(md) {
      flex-direction: row;
      display: flex;
      .nav-link {
        padding-right: 15px;
        color: #333333;
      }
    }
  }
}
</style>
