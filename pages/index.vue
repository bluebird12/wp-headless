<template>
<div class="posts">
  <main>
    <h2>Posts</h2>
  <!-- here we loop through the posts -->
    <div class="post" v-for="post in posts" :key="post.id">
      <h3>
      <!-- for each one of them, we’ll render their title, and link off to their individual page -->
        <a :href="'blog/${post.slug}'">{{ post.title.rendered }}</a>
      </h3>
      <div v-html="post.excerpt.rendered"></div>
      <a :href="'blog/${post.slug}'" class="readmore">Read more ⟶</a>
    </div>
  </main>
  </div>
</template>

<script>
export default {
computed: {
  posts() {
    return this.$store.state.posts;
  },
 },
created() {
  this.$store.dispatch("getPosts");
  }
};
</script>

<style>
.posts {
  display: grid;
  grid-template-columns: 2fr 1fr;
  grid-template-rows: 1fr;
  grid-column-gap: 6vw;
  margin: 5em auto;
  max-width: 80vw;
}
main {
  grid-area: 1 / 1 / 2 / 2;
}
aside {
  grid-area: 1 / 2 / 2 / 3;
}
h2 {
  margin-bottom: 2em;
}
a,
a:active,
a:visited {
  text-decoration: none;
  color: black;
}
a.readmore {
  display: inline-block;
  font-size: 11px;
  text-transform: uppercase;
  padding: 5px 15px;
  letter-spacing: 2px;
  position: relative;
  color: #000;
  font-weight: 700;
  font-family: "Open Sans", serif;
  border: 1px solid #ccc;
  background: #fff;
}
.tags-title {
  background-color: #000;
  color: #fff;
  border: none;
  text-transform: capitalize;
  letter-spacing: 0;
  font-size: 1.2rem;
  padding: 15px;
  margin: 0 35px;
  position: relative;
  top: -25px;
}
.tags-list {
  background: #f5f5f5;
  padding: 70px 25px 25px;
  margin-top: -65px;
}
.post {
  border-bottom: 1px solid rgb(223, 222, 222);
  margin-bottom: 2em;
  padding-bottom: 2em;
  color: #444;
  h3 {
    margin-bottom: 0.5em;
    font-size: 26px;
  }
}
.tags-list ul {
  padding-left: 0;
}
.tags-list li {
  font-family: "Open Sans", serif;
  letter-spacing: 1px;
  text-transform: uppercase;
  padding: 6px 15px;
  margin: 0 0 10px 10px;
  display: inline-block;
  font-size: 0.7rem !important;
  border: 1px solid #000;
  transition: all 0.3s;
  outline: none;
  font-weight: normal;
  cursor: pointer;
  background: #fff;
  a {
    color: #000;
  }
}
.active {
  border: 1px solid #d44119;
  background-color: #fae091 !important;
}
.slide {
  position: relative;
  background: transparent;
  -webkit-transition: 0.3s ease;
  transition: 0.3s ease;
  z-index: 1;
  backface-visibility: hidden;
  perspective: 1000px;
  transform: translateZ(0);
  cursor: pointer;
  &:hover {
    color: #fff;
  }
  &:hover:before {
    right: -1px;
  }
}
.slide::before {
  content: "";
  display: block;
  position: absolute;
  background: #000;
  transition: right 0.3s ease;
  z-index: -1;
  top: -2px;
  bottom: -2px;
  left: -2px;
  right: 108%;
  backface-visibility: hidden;
}
</style>