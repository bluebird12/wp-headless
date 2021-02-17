<template>
  <div class="nav">
    <ul>
      <li>
        <nuxt-link exact to="/">
          <app-icon></app-icon>BlogName
        </nuxt-link>
      </li>
      <li>
        <nuxt-link to="/about">About</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/googlesheet">Google Sheet</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
import AppIcon from "@/components/AppIcon.vue";
export default {
  components: {
    AppIcon
  }
};
</script>

<style scoped>
.nav {
  background: #000;
  color: #fff;
  padding: 1em 100px;
}
.nav a {
    color: #fff;
    opacity: 0.8;
  }
.nav a:hover {
    opacity: 1;
}
div {
  align-items: center;
  display: flex;
  height: 100%;
  width: 100%;
}
ul {
  padding-left: 0;
}

ul li {
display: inline-block;
margin-right: 30px;
}
</style>
