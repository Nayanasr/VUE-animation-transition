<template>
  <modal-ani-transition />
  <h1>Animation and Transition</h1>
  <div class="container">
    <Transition name="slide-fade">
      <div class="block" :class="{ animateLeft: animateBlockLeft }"></div
    ></Transition>
    <button @click="moveLeft">Move Left</button>
  </div>

  <!-- <validate> -->
  <div class="container">
    <Transition name="para">
      <p v-if="paraVisibility">Hey this is a paragraph...</p>
    </Transition>
    <button @click="togglePara">Toggle Paragraph</button>
  </div>

  <!-- modal -->
  <base-modal :modalVisibility="modalVisibility" @hideModal="hideModal">
    <p>Hey i m a modal</p>
    <button @click="hideModal">Close Me</button>
  </base-modal>
  <div>
    <button @click="showModal">Click Modal</button>
  </div>
</template>

<script>
import BaseModal from './components/BaseModal.vue';
// import HelloWorld from "./components/HelloWorld.vue";

export default {
  components: { BaseModal },
  name: "App",
  data() {
    return {
      animateBlockLeft: false,
      paraVisibility: false,
      modalVisibility: false,
    };
  },
  methods: {
    moveLeft() {
      this.animateBlockLeft = !this.animateBlockLeft;
    },
    togglePara() {
      this.paraVisibility = !this.paraVisibility;
    },
    showModal() {
      this.modalVisibility = true;
    },
    hideModal() {
      this.modalVisibility = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.animateLeft {
  /* transform: translateX(-250px); */
  animation: slide-fade 0.5s ease-out forwards;
  /* animation: slide-fade 0.5s ease-out reverse; */
}
.block {
  height: 200px;
  width: 200px;
  background-color: blueviolet;
  margin-bottom: 20px;
  transition: transform 0.5s ease-out;
  border-radius: 100%;
  /* or 50; */
}
.container {
  margin: 2rem auto;
  max-width: 40rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
button {
  background-color: aqua;
  padding: 18px;
  color: blue;
  border-radius: 10px;
}
button:hover {
  background-color: #2c3e50;
  padding: 18px;
  color: bisque;
  border-radius: 20px;
  border: none;
}
.slide-fade-enter-from {
  /* opacity: 0;
  transform: translateY(-40px); */
}
.slide-fade-enter-active {
  /* transition: all 0.5s ease-out; */
  /* to use keyframes */
  animation: slide-fade 0.5s ease-out reverse;
}
.slide-fade-enter-to {
  /* opacity: 1;
  transform: translateY(0); */
}
.slide-fade-leave-from {
  /* opacity: 1;
  transform: translateY(0); */
}
.slide-fade-leave-active {
  /* transition: all 0.3s ease-out; */

  /* to use keyframes */
  animation: slide-fade 0.5s ease-in;
}
.slide-fade-leave-to {
  /* opacity: 0;
  transform: translateY(-40px); */
}

@keyframes slide-fade {
  0% {
    transform: translateX(0) scale(1);
  }
  50% {
    transform: translateX(-125px) scale(1.3);
  }
  100% {
    transform: translateX(-250px) scale(1);
  }
}

.para-enter-from {
  /* opacity: 0;
  transform: translateY(-40px); */
}
.para-enter-active {
  /* transition: all 0.5s ease-out; */
  /* to use keyframes */
  animation: para 0.5s ease-in reverse;
}
.para-enter-to {
  /* opacity: 1;
  transform: translateY(0); */
}
.para-leave-from {
  /* opacity: 1;
  transform: translateY(0); */
}
.para-leave-active {
  /* transition: all 0.3s ease-out; */

  /* to use keyframes */
  animation: para 0.5s ease-in;
}
.para-leave-to {
  /* opacity: 0;
  transform: translateY(-40px); */
}

@keyframes para {
  0% {
    transform: translateY(0) scale(1);
  }
  50% {
    transform: translateY(-125px) scale(1.3);
  }
  100% {
    transform: translateY(-250px) scale(1);
  }
}
</style>