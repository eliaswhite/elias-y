<script setup>
import HeaderComp from "@/components/template/HeaderComp.vue";
</script>

<template>
  <HeaderComp />
  <main>
    <RouterView />
  </main>
</template>

<style>
@import "@/assets/base.css";

#app {
  max-width: 1300px;
  margin: 0 auto;
  height: 110vh;
  font-weight: normal;
}

a {
  color: inherit;
  text-decoration: none;
}

footer {
  height: 10%;
  color: white;
  font-size: 1.3rem;
  display: flex;
  align-items: center;
  padding-left: 20px;
}

header span {
  padding: 0 20px;
}
</style>
