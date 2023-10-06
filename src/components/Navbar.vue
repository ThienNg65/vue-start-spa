<template>
  <nav
    :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-sm']"
  >
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Vue</a>
      <!-- Links -->
      <ul class="navbar-nav">
        <li v-for="(page, index) in pages" class="nav-item" :key="index">
          <navbar-link
            :page="page"
            :isActive="activePage === index"
            @click.prevent="navLinkClick(index)"
          >
          </navbar-link>
        </li>
      </ul>
      <form class="d-flex">
        <button class="btn btn-primary" @click.prevent="changeTheme()">
          Toggle
        </button>
      </form>
    </div>
  </nav>
</template>

<script>
import NavbarLink from "./NavbarLink.vue";
export default {
  components: {
    NavbarLink,
  },
  props: ["pages", "activePage", "navLinkClick"],

  data() {
    return {
      theme: "light",
    };
  },
  methods: {
    changeTheme() {
      this.theme = this.theme === "light" ? "dark" : "light";
    },
  },
};
</script>
