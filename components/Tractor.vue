<template>
  <img class="tractorMove" width="120px" src="~/assets/Tractor-icon.svg" />
</template>

<script>
export default {}
</script>

<style>
.tractorMove {
  transform: translateX(0px);
  animation: turn 3.5s ease-out forwards 5s;
}

@keyframes turn {
  100% {
    transform: translateX(800px);
  }
}
</style>