<template>
  <div id="app">
    <div class="content">
      <embla-carousel option="{ loop: true }">
        <embla-slide v-for="n in 5" v-bind:key="n"></embla-slide>
      </embla-carousel>
    </div>
    <app-footer/>
  </div>
</template>

<script>

export default {
  name: "App",
};
</script>