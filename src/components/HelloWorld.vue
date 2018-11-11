<template>
  <div>
    <div class="row mb-5">
      <div class="col d-flex justify-content-center">
        <img alt="Vue logo" src="./../assets/logo.png">
      </div>
    </div>

    <div class="row">
      <div class="col">
        <h1 class="text-center">{{ msg }}</h1>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    props: {
      msg: String
    }
  }
</script>

<style scoped lang="scss">
</style>
