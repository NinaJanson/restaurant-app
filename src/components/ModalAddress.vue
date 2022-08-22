<template>
  <transition name="modal-animation">
    <div class="modal">
      <transition name="modal-animation-inner">
        <details class="modal-content">
          <summary>See address...</summary>
          <slot />
          <button @click="$emit('closeModal')" class="close-btn">✖️</button>
        </details>
      </transition>
    </div>
  </transition>
</template>

<script>
export default {
  name: "ModalAddress",
  emits: ["closeModal"],
};
</script>
<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 999;
  background: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  position: relative;
  background: white;
  width: 70vw;
  _height: 30vh;
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
  box-shadow: rgba(6, 24, 44, 0.4) 0px 0px 0px 2px,
    rgba(6, 24, 44, 0.65) 0px 4px 6px -1px,
    rgba(255, 255, 255, 0.08) 0px 1px 0px inset;
}

summary {
  _padding: 2rem;
  margin: 1rem;
}
.close-btn {
  all: unset;
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  cursor: pointer;
  border: solid black 1px;
  border-radius: 50%;
  background-color: rgba(0, 0, 0, 0.8);
  padding: 2px;
}

.modal-animation-enter-active,
.modal-animation-leave-active {
  transition: opacity 0.4s linear;
}
.modal-animation-enter-from,
.modal-animation-leave-to {
  opacity: 0;
}

.modal-animation-inner-enter-active,
.modal-animation-inner-leave-active {
  transition: all 0.4s linear;
}
.modal-animation-inner-enter-from,
.modal-animation-inner-leave-to {
  opacity: 0;
  transform: scale(0.8);
}
</style>
