<template>
  <div>
    <nav class="navbar bg-base-100">
      <Brand :class="[isSmall ? 'hidden' : 'navbar-start']" />
      <div :class="[isSmall ? 'navbar-start' : 'navbar-center']">
        <div :class="[isSmall ? 'dropdown' : 'navbar-center flex']">
          <label tabindex="0" class="btn btn-ghost lg:hidden">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-5 w-5"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h8m-8 6h16"
              />
            </svg>
          </label>
          <ul
            tabindex="0"
            :class="[
              isSmall
                ? 'menu menu-compact dropdown-content mt-3 p-2 shadow bg-base-100 rounded-box w-52'
                : 'menu menu-horizontal p-0',
            ]"
          >
            <li>
              <router-link to="/">Home</router-link>
            </li>
            <li>
              <router-link to="/about">About</router-link>
            </li>
          </ul>
        </div>
      </div>
      <Brand :class="[isSmall ? 'navbar-center' : 'hidden']" />
      <div class="navbar-end">
        <div class="dropdown dropdown-end">
          <label tabindex="0" class="btn btn-ghost btn-circle">
            <div class="indicator">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-5 w-5"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"
                />
              </svg>
              <span class="badge badge-sm indicator-item">
                {{ chart.itemTotal }}
              </span>
            </div>
          </label>
          <div
            tabindex="0"
            class="
              mt-3
              card card-compact
              dropdown-content
              w-52
              bg-base-100
              shadow
            "
          >
            <div class="card-body">
              <span class="font-bold text-lg">{{ chart.itemTotal }} Items</span>
              <span class="text-info">Subtotal: Rp. {{ chart.subTotal }}</span>
              <div class="card-actions">
                <button class="btn btn-primary btn-block">View cart</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
import Brand from "./Brand.vue";
export default {
  name: "Navbar",
  components: { Brand },
  data() {
    return {
      isSmall: true,
      chart: {
        itemTotal: 0,
        subTotal: 0,
      },
    };
  },
  methods: {
    toggleLarge() {
      if (window.innerWidth < 1024) {
        this.isSmall = true;
      } else {
        this.isSmall = false;
      }
    },
  },
  created() {
    window.addEventListener("resize", this.toggleLarge);
  },
  destroyed() {
    window.removeEventListener("resize", this.toggleLarge);
  },
};
</script>

<style>
</style>