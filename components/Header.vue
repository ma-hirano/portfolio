<template>
  <div class="bgcolor-fo">
    <b-nav class="align-items-center p-2">
      <b-navbar-brand class="fs25r m-2 p-0 pr-1 pb-2 color-white" tag="h1">Portfolio</b-navbar-brand>
      <ul class="p-0">
              <li class="inline-block">
                <nuxt-link
                  to="/"
                  :class="[navbar_a]"
                  class=""
                >Home
                </nuxt-link>
              </li>
              <li class="inline-block">
                <nuxt-link
                  to="/space"
                  :class="[navbar_a]"
                  class="ml-1"
                >Space
                </nuxt-link>
              </li>
              <li class="inline-block">
                <nuxt-link
                  to="/wordlePage"
                  :class="[navbar_a]"
                  class="ml-1"
                >Wordle
                </nuxt-link>
              </li>
      </ul>
    </b-nav>
  </div>
</template>

<script>
export default {
  data() {
  return {
    navbar_a: 'block fs18r px-4 py-2 m-0 color-white fw500 text-decoration-none',
  }
}
};
</script>

<style>
  a:hover {
    color: white;
  }
</style>
