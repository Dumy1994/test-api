<template>
  <section class="container-spinner">
    <div class="spinner" >
      <div class="head"></div>
    </div>
  </section>
</template>

<script>
export default {
  name: "AppLoader",

  data() {
    return {};
  },
};
</script>

<style>
.container-spinner{
  width: 100%;
  height: 90vh;
  margin-top: 5vh;
}
.spinner {
  width: 10em;
  height: 10em;
  border-top: 1em solid rgb(29, 189, 136);
  border-right: 1em solid transparent;
  border-radius: 50%;
  margin: auto;
  animation: spinner 0.6s linear infinite;
  font-size: 18px
}
.head {
  width: 1em;
  height: 1em;
  background-color: rgb(29, 189, 136);
  border-radius: 50%;
  margin-left: 8.5em;
  margin-top: 0.5em;
}
@keyframes spinner {
  100% {
    transform: rotate(360deg);
  }
}
</style>