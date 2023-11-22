<template>
  <h1>Home</h1>
  <nav class="navigation1">
    <router-link
      to="/quiz"
      class="navigation__link1"
      exact-active-class="navigation__link--exact-active1"
      >Vue クイズ</router-link
    >/
    <router-link
      to="/palette"
      class="navigation__link1"
      exact-active-class="navigation__link--exact-active1"
      >Vue パレット</router-link
    >/
    <router-link
      to="/memo"
      class="navigation__link1"
      exact-active-class="navigation__link--exact-active1"
      >Vue メモ</router-link
    >
  </nav>
</template>

<style>
.navigation1 {
  display: flex;
  font-style: italic;
  align-items: flex-end;
  gap: 0.8rem;
  font-size: 1.5rem;
}

.navigation__link1 {
  font-weight: bold;
  color: blue;
}

.navigation__link--exact-active1 {
  color: #42b983;
}
</style>
