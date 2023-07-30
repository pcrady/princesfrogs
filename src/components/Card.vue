<template>
  <transition name="fade">
    <div class="scene face-component" v-if="isVisible">
      <div class="card" :class="{ 'is-flipped': isFlipped }">
        <div class="card__face card__face--front">
          <div v-if="cardType === 1" class="card-type-1-front">
            <i class="fa-solid fa-4x" 
               style="color: #ffb302; 
                      rotate: -45deg; 
                      position: absolute; 
                      top: 45px; 
                      left: -15px">&#xf521;
            </i>
            <i class="fa-solid fa-10x" 
               style="color: #ffb302; 
                      rotate: 270deg; 
                      position: absolute; 
                      top: 50px; 
                      left: 15px">&#xf521;
            </i>
            <i class="fa-solid fa-2x" 
               style="color: #f1e3a4; 
                      position: absolute; 
                      top: 10px; 
                      left: 10px">&#xf005;
            </i>
            <i class="fa-solid fa-3x" 
               style="color: #f1e3a4; 
                      position: absolute; 
                      rotate: 30deg;
                      top: 5x; 
                      left: 80px">&#xf005;
            </i>
            <i class="fa-solid" 
               style="color: #f1e3a4; 
                      position: absolute; 
                      rotate: 30deg;
                      top: 70px; 
                      font-size: 2em;
                      left: 65px">&#xf005;
            </i>
            <i class="fa-solid" 
               style="color: #f1e3a4; 
                      position: absolute; 
                      rotate: 30deg;
                      top: 170px; 
                      font-size: 1.7em;
                      left: 100px">&#xf005;
            </i>
            <i class="fa-solid" 
               style="color: #f1e3a4; 
                      position: absolute; 
                      rotate: 30deg;
                      top: 135px; 
                      font-size: 3.5em;
                      left: 15px">&#xf005;
            </i>
            <i class="fa-regular" 
               style="color: #eeeeec; 
                      position: absolute; 
                      top: 142px; 
                      font-size: 2em;
                      left: 95px">&#x2a;
            </i>
            <i class="fa-regular" 
               style="color: #eeeeec; 
                      position: absolute; 
                      rotate: 100deg;
                      top: 70px; 
                      font-size: 1.5em;
                      left: 87px">&#x2a;
            </i>
            <i class="fa-regular" 
               style="color: #eeeeec; 
                      position: absolute; 
                      rotate: 30deg;
                      top: 80px; 
                      left: 25px;
                      font-size: 1em;">&#x2a;
            </i>
            <!-- <i class="crown-large fa-solid fa-10x fa-rotate-270" style="color: #ffb302;">&#xf521;</i> -->
         </div>
          <div v-else-if="cardType === 2" class="card-type-2-front">
          
          </div>
        </div>
        <div class="card__face card__face--back">
          <div v-if="cardType === 1" class="card-type-1-back">
              <p>THIS IS CARD TYPE 1</p>
          </div>
          <div v-else-if="cardType === 2" class="card-type-2-back">
              <p>THIS IS CARD TYPE 2</p>
          </div>
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
    'frontLabel',
    'backLabel',
    'cardType',
  ],
};
</script>

<style>
.scene {
  width: 175px;
  height: 245px;
  perspective: 600px;
  padding: 1em;
  overflow: hidden;
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
  /* background-color: #e0d35b; */
  padding: 10px; 
  border: 1px solid black;
  box-shadow: inset 0 0 0 10px #ffb302;
  overflow: hidden;
}

.card__face--front {
  background-color: #e78e6a;
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
  overflow:hidden;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

.card-type-1-front {
  background-color: #faf9d0;
  width: 100%;
  height: 100%;
}


.card-type-2-front {

}


.card-type-1-back {

}

.card-type-2-back {

}

</style>

