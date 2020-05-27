<template>
  <div>
    <section class="app__header">
      <b-navbar toggleable="lg" type="dark" variant="info">
        <b-navbar-brand href="/">Damon Jokes</b-navbar-brand>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item href="/">Home</b-nav-item>
            <b-nav-item href="/jokes">Jokes</b-nav-item>
            <b-nav-item href="/about">About</b-nav-item>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </section>
  </div>
</template>

<script>
  export default {
    name: 'AppHeader'
  }

</script>

<style scoped>

</style>
