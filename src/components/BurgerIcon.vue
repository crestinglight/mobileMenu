<template>
    <a href="#" class="burger__icon">
      <div class="burger__line bacon"></div>
      <div class="burger__line lettuce"></div>
      <div class="burger__line tomato"></div>
    </a>
</template>

<script>
// import gsap from "gsap";

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted(){
    // gsap.to(".burger__line", {
    //   ease: "power2.out",
    //   duration: 3,
    //   x: "-500px",
    //   repeat: 0
    // })
  }
}
</script>

<style scoped>
.burger__icon {
  display: block;
  padding: 12px 16px;
}

.burger__line {
  width: 40px;
  height: 8px;
  background-color: #51007A;
  margin: 4px 0;
  transform: skewX(38deg);
}
</style>
