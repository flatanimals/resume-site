<template>
  <div class="notfound">
    <div class="notfound-overlay">
      <h1 class="notfound-message">404</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "not-found"
};
</script>

<style lang="postcss">
.notfound {
  @apply w-screen;
  @apply h-screen;
  @apply bg-no-repeat;
  @apply bg-cover;
  @apply bg-black;
  background-position: center;
  background-image: url("/imgs/404.jpg");
}
.notfound-overlay {
  @apply w-screen;
  @apply h-screen;
  @apply flex;
  @apply flex-col;
  @apply items-center;
  @apply justify-center;
  background: linear-gradient(transparent, rgba(0, 0, 0, 0.55), transparent);
}
.notfound-message {
  @apply font-extrabold;
  @apply text-center;
  @apply text-white;
  font-size: 108px;
  text-shadow: 0px 2px 3px rgba(0, 0, 0, 0.75);
}
</style>
