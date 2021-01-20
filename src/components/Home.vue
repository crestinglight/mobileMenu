<template>
    <div class="page">
        <h1>Home</h1>
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.page {
    display: flex;
    flex-direction: column;
    flex: 1;
    justify-content: center;
    align-items: center;
    background-image: linear-gradient(to bottom right, #51007A, #E70941);
    color: white;
}
</style>
