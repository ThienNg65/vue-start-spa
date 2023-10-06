<template>
  <nav
    :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-sm']"
  >
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Vue</a>
      <!-- Links -->
      <ul class="navbar-nav">
        <li v-for="(page, index) in pages" class="nav-item" :key="index">
          <a
            class="nav-link"
            :class="{ active: activePage == index }"
            aria-current="page"
            :href="page.link.url"
            :title="`This link goes to the ${page.link.text} page`"
            @click.prevent="navLinkClick(index)"
            >{{ page.link.text }}
          </a>
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
export default {
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
