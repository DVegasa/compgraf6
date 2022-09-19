<template>
  <div class="container mt-4">
    <ul>
      <router-link class="link" to="/lab_1"
        ><li>Лабораторная 1</li></router-link
      >
      <router-link class="link" to="/lab_2"
        ><li>Лабораторная 2</li></router-link
      >
      <router-link class="link" to="/lab_3"
        ><li>Лабораторная 3</li></router-link
      >
      <router-link class="link" to="/lab_4"
        ><li>Лабораторная 4</li></router-link
      >
      <router-link class="link" to="#" disabled
        ><li><s>Лабораторная 5</s></li></router-link
      >
      <router-link class="link" to="/lab_6"
        ><li>Лабораторная 6</li></router-link
      >
    </ul>
  </div>
</template>

<style lang="sass">
.container
  font-size: 20px
</style>
