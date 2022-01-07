<template>
  <button @click="handleClick" class="bg-blue-500">start button</button>
  <button @click="handleOtherClick" class="bg-red-500 fixed right-0">Leave Button</button>

  <div id="title-field" class="absolute flex flex-col top-[35%] left-[20%] w-[70vh]">
    <h1 ref="lineone" class="title opacity-0">Hello</h1>
    <div ref="linecoverone" class="titlecover change w-0 mt-[.5vh]"></div>
    <h1 ref="linetwo" class="title opacity-0">Darkness</h1>
    <div ref="linecovertwo" class="titlecover change w-0 mt-[9.5vh]"></div>
    <h1 ref="linethree" class="title opacity-0">my</h1>
    <div ref="linecoverthree" class="titlecover change w-0 mt-[18.5vh]"></div>
    <h1 ref="linefour" class="title opacity-0">Old friend</h1>
    <div ref="linecoverfour" class="titlecover change w-0 mt-[27.5vh]"></div>
  </div>
  <!-- <HelloWorld msg="Hello Vue 3 + Vite" /> -->
</template>

<script>
import { ref } from '@vue/reactivity';
import { onMounted } from '@vue/runtime-core';
export default {
  name: 'Title',
  setup() {
    console.log('hi');

    const lineone = ref(null)
    const linecoverone = ref(null)
    const linetwo = ref(null)
    const linecovertwo = ref(null)
    const linethree = ref(null)
    const linecoverthree = ref(null)
    const linefour = ref(null)
    const linecoverfour = ref(null)
    let titleActive = false;

    const timedifference = 75;
    const timertwo = timedifference * 2;
    const timerthree = timedifference * 3;
    const timerfour = timedifference * 4;
    const covertime = 500; // same as transiton attribute of change class!!

    const handleClick = () => {

      console.log('somethin');

      titleActive = true;

      // left to right line fill space
      linecoverone.value.classList.remove("w-0")
      linecoverone.value.classList.add("w-full")

      setTimeout(() => {
        linecovertwo.value.classList.remove("w-0")
        linecovertwo.value.classList.add("w-full")
      }, timertwo)

      setTimeout(() => {
        linecoverthree.value.classList.remove("w-0")
        linecoverthree.value.classList.add("w-full")
      }, timerthree)

      setTimeout(() => {
        linecoverfour.value.classList.remove("w-0")
        linecoverfour.value.classList.add("w-full")
      }, timerfour)

      // show text
      setTimeout(() => {
        lineone.value.classList.toggle("opacity-100")
        linecoverone.value.classList.add("right-0")
        linecoverone.value.classList.remove("w-full")
        linecoverone.value.classList.add("w-[36.5vh]")
      }, covertime);

      setTimeout(() => {
        linetwo.value.classList.toggle("opacity-100")
        linecovertwo.value.classList.add("right-0")
        linecovertwo.value.classList.remove("w-full")
        linecovertwo.value.classList.add("w-[14.7vh]")
      }, timertwo + covertime);

      setTimeout(() => {
        linethree.value.classList.toggle("opacity-100")
        linecoverthree.value.classList.add("right-0")
        linecoverthree.value.classList.remove("w-full")
        linecoverthree.value.classList.add("w-[52.7vh]")
      }, timerthree + covertime);

      setTimeout(() => {
        linefour.value.classList.toggle("opacity-100")
        linecoverfour.value.classList.add("right-0")
        linecoverfour.value.classList.remove("w-full")
        linecoverfour.value.classList.add("w-[9vh]")
      }, timerfour + covertime);
    }

    const handleOtherClick = () => {
      console.log(linecoverone.value.classList);
      // left to right line fill space
      linecoverone.value.classList.remove("w-[36.5vh]")
      linecoverone.value.classList.add("w-full")

      setTimeout(() => {
        linecovertwo.value.classList.remove("w-[14.7vh]")
        linecovertwo.value.classList.add("w-full")
      }, timertwo)

      setTimeout(() => {
        linecoverthree.value.classList.remove("w-[52.7vh]")
        linecoverthree.value.classList.add("w-full")
      }, timerthree)

      setTimeout(() => {
        linecoverfour.value.classList.remove("w-[9vh]")
        linecoverfour.value.classList.add("w-full")
      }, timerfour)

      // hide text
      setTimeout(() => {
        lineone.value.classList.toggle("opacity-100")
        linecoverone.value.classList.remove("right-0")
        linecoverone.value.classList.remove("w-full")
        linecoverone.value.classList.add("w-0")
      }, covertime);

      setTimeout(() => {
        linetwo.value.classList.toggle("opacity-100")
        linecovertwo.value.classList.remove("right-0")
        linecovertwo.value.classList.remove("w-full")
        linecovertwo.value.classList.add("w-0")
      }, timertwo + covertime);

      setTimeout(() => {
        linethree.value.classList.toggle("opacity-100")
        linecoverthree.value.classList.remove("right-0")
        linecoverthree.value.classList.remove("w-full")
        linecoverthree.value.classList.add("w-0")
      }, timerthree + covertime);

      setTimeout(() => {
        linefour.value.classList.toggle("opacity-100")
        linecoverfour.value.classList.remove("right-0")
        linecoverfour.value.classList.remove("w-full")
        linecoverfour.value.classList.add("w-0")
      }, timerfour + covertime);

      }

    onMounted(() => {
      setTimeout(() => {
        handleClick()
      }, 100)
    })

    return { linefour, linecoverfour, linethree, linecoverthree, linetwo, linecovertwo, lineone, linecoverone, handleClick, handleOtherClick }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Work+Sans:wght@900&display=swap');

h1 {
  font-family: 'Work Sans', sans-serif;
}

.change {
  transition: width .5s ease-out;
}
</style>
