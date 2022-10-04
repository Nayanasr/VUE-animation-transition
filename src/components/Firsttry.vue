<template>

  <h1>HELLO</h1>
  <div class="container">
    <div class="block" :class="{animateLeft:animateBlockLeft}"></div>
    <button @click="moveLeft">MOVE LEFT</button>
  </div>

  <div class="container">
    <Transition name="para">
      <p v-if="paraVisibility">HEY! THIS IS A PARAGRAPH.......</p>
    </Transition>
    <button @click="togglePara">TOGGLE PARAGRAPH</button>
  </div>

  

</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      animateBlockLeft: false,
      paraVisibility:false
    };
  },
  methods: {
    moveLeft(){
      this.animateBlockLeft = !this.animateBlockLeft
    },
    togglePara(){
      this.paraVisibility = !this.paraVisibility
    }
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
.animateLeft{
  /* transform: translateX(-250px) */
  animation: slide-fade 0.5s ease-out forwards;
    /* animation: slide-fade 0.5s ease-out reverse; for reverse slide */

}
.block{
  height: 200px;
  width: 200px;
  background-color: black;
  margin-bottom: 20px;
  /* transition: transform 0.5s ease-out; */
}
.container{
  margin: 2rem auto;
  max-width: 40rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
button{
  background-color: red;
  padding: 18px;
  color: greenyellow;
  border-radius: 10px;
}
button:hover{
  background-color: blue;
  padding: 18px;
  color: cornflowerblue;
  border-radius: 10px;
}

.para-enter-from{
  /* opacity: 0;
  transform: translateY(-40px); */
}
.para-enter-active{
  /* transition: all 0.8s ease-out; */
    /* to use keyframes */
   animation: para 0.5s ease-in reverse;
}
.para-enter-to{
  /* opacity: 1;
  transform: translateY(0); */
}
.para-leave-from{
  /* opacity: 1;
  transform: translateY(0); */
}
.para-leave-active{
  /* transition: all 0.3s ease-out; */

  /* to use keyframes */
  animation: para 0.5s ease-in;
}
.para-leave-to{
  /* opacity: 0;
  transform: translateY(-40px); */
}

  /* to use keyframes for para */

@keyframes para{
  0%{
    transform: translateY(0) scale(1);
  }
  50%{
    transform: translateY(-125px) scale(1,3);
  }
  100%{
    transform: translateY(-250px) scale(1);
  }
}

/* to use keyframes for slide show */
@keyframes slide-fade{
  0%{
    transform: translate(0) scale(1);
  }
  50%{
    transform: translate(-125px) scale(1,3);
  }
  100%{
    transform: translate(-250px) scale(1);
  }
}
</style>
