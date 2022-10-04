<template>
  <div
    v-if="modalVisibility"
    @click="$emit('hideModal')"
    class="backdrop"
  ></div>
  <transition name="modal">
    <dialog v-if="modalVisibility" open>
      <slot></slot>
    </dialog>
  </transition>
  <!-- </div> -->
</template>

<script>
export default {
  props: ["modalVisibility"],
  emits: ["hideModal"],
};
</script>

<style>
dialog {
  position: fixed;
  top: 80px;
  width: 32%;
  height: 18%;
  border: none;
  box-shadow: 0 3px 8px rgba(0, 0, 0, 0.4);
  border-radius: 13px;
  z-index: 100;
  /* animation: modal 0.5s ease-out forwards; */
}
.backdrop {
  position: fixed;
  top: 0;
  width: 100%;
  height: 100vh;
  z-index: 50;
  background-color: rgba(0, 0, 0, 0.5);
}
.modal-enter-active {
  animation: modal 0.5s ease-out;
}
.modal-leave-active {
  animation: modal 0.5s ease-in reverse;
}

@keyframes modal {
  from {
    opacity: 0;
    transform: translateY(-40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>