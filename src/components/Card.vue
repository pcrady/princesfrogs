<template>
  <transition name="fade">
    <div class="scene face-component" v-if="isVisible">
      <div class="card" :class="{ 'is-flipped': isFlipped }">
        <div class="card__face card__face--front">
          <slot name="front"></slot>
          <p>{{ label }}</p>
        </div>
        <div class="card__face card__face--back">
          <slot name="back"></slot>
          <p>{{ label }}</p>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props: [
    'isFlipped',
    'isVisible',
    'label',
  ],
};
</script>

<style>
.scene {
  width: 175px;
  height: 245px;
  perspective: 600px;
  padding: 1em;
}

.card {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 1s;
  transform-style: preserve-3d;
}

.card.is-flipped {
  transform: rotateY(180deg);
}

.card__face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
}

.card__face--front {
  background-color: #bbb;
}

.card__face--back {
  background-color: #dbd;
  transform: rotateY(180deg);
}

.fade-component {
  width: 200px;
  height: 200px;
  background: #3498db;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>

