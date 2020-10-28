<template>
  <h1 @click="onClick">
    {{message}}
  </h1>
</template>

<script>

import Vue from 'vue';
import Component from 'vue-class-component';

export default Component({})(
  class App extends Vue {
    message = 'Batman';
    onClick() {
      this.message = 'Bruce Wayne';
    }
  }
);
</script>