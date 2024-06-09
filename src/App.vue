<!-- eslint-disable no-unused-vars -->
<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import { reactive } from 'vue'
import { useAuthStore } from './stores/auth'


const auth = useAuthStore()

const data = reactive({
  variable1: 'Test Variable',
  counter: 1,
  varibale2: [1, 2, 3, 4, 5]
})

const tambahCounter = () => {
  data.counter++
}

function kurangCounter() {
  data.counter--
}
</script>

<template>
  <!-- <navbar /> -->
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo_bank.png" width="125" height="125" />

    <div class="wrapper">
      <Header :text="'selamat datang   '">
      </Header>
      <Header :text="'BANK HS'"></Header>
      <!--HelloWorld msg="menabung=mengurangi sampah sekali pakai" /-->
      <h2>kurangi sampah sekali pakai</h2>
      <nav>
        <RouterLink v-if="auth.isLoggedIn" to="/">Home</RouterLink>
        <RouterLink v-if="auth.isLoggedIn" to="/about">About</RouterLink>
        <RouterLink v-if="!auth.isLoggedIn" to="/login">Login</RouterLink>
        <RouterLink v-if="auth.isLoggedIn" to="/Transfer">Transfer</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;

  color: rgb(10, 0, 2);
}

.logo {
  display: block;
  margin: 0 auto 2rem;
  border-radius: 50%; 
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
