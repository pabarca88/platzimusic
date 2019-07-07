<template>
  <div class="wrap-load">
    <div class="loader">Loading...</div>
  </div>
</template>

<script>
export default {
  name: 'spinner'
}
</script>

<style lang="css" scoped>
.wrap-load {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(255,255,255,0.8);
  display: flex;
  justify-content: center;
  align-items: center;
}
.loader,
.loader:after {
  border-radius: 50%;
  width: 10em;
  height: 10em;
  position: fixed;
}
.loader {
  margin: 60px auto;
  font-size: 10px;
  position: relative;
  text-indent: -9999em;
  border-top: 1.1em solid rgba(255,112,108, 0.2);
  border-right: 1.1em solid rgba(255,112,108, 0.2);
  border-bottom: 1.1em solid rgba(255,112,108, 0.2);
  border-left: 1.1em solid #ff706c;
  -webkit-transform: translateZ(0);
  -ms-transform: translateZ(0);
  transform: translateZ(0);
  -webkit-animation: load8 1.1s infinite linear;
  animation: load8 1.1s infinite linear;
}
@-webkit-keyframes load8 {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
@keyframes load8 {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}

</style>
