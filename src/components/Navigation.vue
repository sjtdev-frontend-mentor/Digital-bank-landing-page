<template>
  <nav class="fixed inset-0 z-100 mx-auto flex h-[64px] w-full max-w-[1100px] items-center justify-between bg-white px-[20px] lg:h-[80px]">
    <img class="h-[24px]" src="/images/logo.svg" alt="" />
    <ul class="top-menu text-grayish-blue absolute hidden h-[80px] w-full items-center justify-center gap-[24px] lg:flex">
      <li class="h-full"><a class="block h-full border-b-4 border-transparent leading-[80px]" href="#">Home</a></li>
      <li class="h-full"><a class="block h-full border-b-4 border-transparent leading-[80px]" href="#">About</a></li>
      <li class="h-full"><a class="block h-full border-b-4 border-transparent leading-[80px]" href="#">Contact</a></li>
      <li class="h-full"><a class="block h-full border-b-4 border-transparent leading-[80px]" href="#">Blog</a></li>
      <li class="h-full"><a class="block h-full border-b-4 border-transparent leading-[80px]" href="#">Careers</a></li>
    </ul>
    <RequestInviteButton class="z-100 hidden lg:block" />
    <button @click="isMenuOpen = !isMenuOpen" class="flex h-[24px] w-[24px] items-center justify-center lg:hidden">
      <img v-if="!isMenuOpen" src="/images/icon-hamburger.svg" alt="" />
      <img v-else src="/images/icon-close.svg" alt="" />
    </button>
    <Transition name="mask">
      <div v-show="isMenuOpen" @click="isMenuOpen = false" class="bg-dark-blue/60 absolute inset-0 top-[64px] h-[100dvh] mask-b-from-50%"></div>
    </Transition>
    <Transition name="nav">
      <ul v-show="isMenuOpen" class="text-dark-blue menu absolute inset-0 top-[64px] z-50 m-[24px] flex h-[264px] w-auto flex-col items-center justify-center gap-[24px] rounded-sm bg-white text-base">
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Contact</a></li>
        <li><a href="#">Blog</a></li>
        <li><a href="#">Careers</a></li>
      </ul>
    </Transition>
  </nav>
</template>

<script setup lang="ts">
import { ref } from "vue";
import RequestInviteButton from "./RequestInviteButton.vue";

const isMenuOpen = ref(false);
</script>

<style scoped>
.nav-enter-active,
.nav-leave-active {
  z-index: 0;
  transition: all 300ms ease-in-out;
}
.nav-enter-from,
.nav-leave-to {
  transform: translateY(-32px);
  opacity: 0;
}

.mask-enter-active,
.mask-leave-active {
  transition: opacity 300ms ease-in-out;
}

.mask-enter-from,
.mask-leave-to {
  opacity: 0;
}

.top-menu a:hover {
  color: var(--color-dark-blue);
  /* 备用单色边框 */
  border-bottom: 4px solid var(--color-lime-green);
  border-bottom: 4px solid;
  border-image: linear-gradient(to right, var(--color-lime-green), var(--color-bright-cyan)) 4;
}
</style>
