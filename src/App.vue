<template>
  <the-header title="Some Title" />
  <router-view/>
</template>

<script>
import TheHeader from '@/components/layouts/TheHeader'
export default {
  components: {
    TheHeader
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
}
</style>
