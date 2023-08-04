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
         </div>
          <div v-else-if="cardType === 2" class="card-type-2-front">
            <span style = "display: inline-block;
                  transform: scaleX(0.5);">            
               <i class="fa-solid" 
               style="color: #80cd70; 
                      position: absolute;
                      rotate: 10deg;
                      top: -20px; 
                      left: -12px;
                      font-size: 11.5em;
                      ">&#xf004;
            </i></span>
            <span style = "display: inline-block;
                  transform: scaleX(1.2);">           
               <i class="fa-solid" 
               style="color: #8cb05c; 
                      position: absolute;
                      rotate: 15deg;
                      top: 60px; 
                      left: 20px;
                      font-size: 5em;
                      ">&#xf004;
            </i> </span>
            <span style = "display: inline-block;
                  transform: scaleX(0.5);">            
               <i class="fa-solid" 
               style="color: #80cd70; 
                      position: absolute;
                      rotate: 15deg;
                      top: 90px; 
                      left: 130px;
                      font-size: 6em;
                      ">&#xf004;
            </i></span>
            <span style = "display: inline-block;
                  transform: scaleX(0.4);">            
               <i class="fa-regular" 
               style="color: #7fa44f; 
                      position: absolute;
                      rotate: 15deg;
                      top: 60px; 
                      left: -10px;
                      font-size: 6em;
                      ">&#xf004;
            </i></span>
            <span style = "display: inline-block;
                  transform: scaleX(.6);">           
               <i class="fa-solid" 
               style="color: #8cb05c; 
                      position: absolute;
                      rotate: 15deg;
                      top: -15px; 
                      left: 0px;
                      font-size: 2em;
                      ">&#xf004;
            </i> </span>
            <span style = "display: inline-block;
                  transform: scaleX(.6);">           
               <i class="fa-regular" 
               style="color: #eeeeec; 
                      position: absolute;
                      rotate: 15deg;
                      top: -15px; 
                      left: 0px;
                      font-size: 2em;
                      ">&#xf004;
            </i> </span>
            <img src="./icons/spiral(5).png" 
                 style=" 
                      position: absolute; 
                      rotate: 240deg;
                      width: 45px;
                      top: 110px; 
                      left: 0px;">
            <img src="./icons/spiral(5).png" 
                 style=" 
                      position: absolute; 
                      rotate: 80deg;
                      width: 60px;
                      top: 3px; 
                      left: 83px;">
            <img src="./icons/spiral(5).png" 
                 style=" 
                      position: absolute; 
                      rotate: 70deg;
                      width: 65px;
                      top: 145px; 
                      left: 75px;">
              <div 
              style="
              position:absolute; 
              top: 40px;
              left: 25px;
              "> 
                <p style=
                  "color:#eeeeec;
                  font-weight: bold;
                  font-family: Times New Roman;
                  font-size:small;">
                  His best quality<br>is...</p></div>
          </div>
          <div v-else-if="cardType === 3" class="card-type-3-front">           
            <i class="fa-regular" 
            style="color: #eeeeec; 
                  position: absolute;
                  rotate: 10deg;
                  top: -6px; 
                  left: -15px;
                  font-size: 9.5em;
                  ">&#xf005;
                  </i>
            <i class="fa-regular" 
            style="color: #277dfe; 
                  position: absolute;
                  rotate: 10deg;
                  top: -2px; 
                  left: -11px;
                  font-size: 9em;
                  ">&#xf005;
                  </i>
            <i class="fa-solid" 
            style="color: #a9cbfe; 
                  position: absolute;
                  rotate: -20deg;
                  top: 60px; 
                  left: -10px;
                  font-size: 8.5em;
                  ">&#xf186;
                  </i>
            <i class="fa-regular" 
            style="color: #eeeeec; 
                  position: absolute;
                  rotate: 186deg;
                  top: 5px; 
                  left: 65px;
                  font-size: 2.5em;
                  ">&#xf005;
                  </i>
            <i class="fa-solid" 
            style="color: #70a9fe; 
                  position: absolute;
                  rotate: 186deg;
                  top: 8.5px; 
                  left: 68px;
                  font-size: 2.1em;
                  ">&#xf005;
                  </i>
            <i class="fa-regular" 
            style="color: #eeeeec; 
                  position: absolute;
                  rotate: -15deg;
                  top: 95px; 
                  left: 65px;
                  font-size: 3.5em;
                  ">&#xf005;
                  </i>
            <i class="fa-solid" 
            style="color: #70a9fe; 
                  position: absolute;
                  rotate: -15deg;
                  top: 98px; 
                  left: 68px;
                  font-size: 3.1em;
                  ">&#xf005;
                  </i>
            <i class="fa-regular" 
            style="color: #eeeeec; 
                  position: absolute;
                  rotate: -15deg;
                  top: 105px; 
                  left: 25px;
                  font-size: 1.9em;
                  ">&#xf005;
                  </i>
            <i class="fa-solid" 
            style="color: #70a9fe; 
                  position: absolute;
                  rotate: -15deg;
                  top: 108px; 
                  left: 27.5px;
                  font-size: 1.6em;
                  ">&#xf005;
                  </i>
            <i class="fa-regular" 
            style="color: #eeeeec; 
                  position: absolute;
                  rotate: 17deg;
                  top: 150px; 
                  left: 85px;
                  font-size: 3em;
                  ">&#xf005;
                  </i>
            <i class="fa-solid" 
            style="color: #277dfe; 
                  position: absolute;
                  rotate: 17deg;
                  top: 153.5px; 
                  left: 88px;
                  font-size: 2.6em;
                  ">&#xf005;
                  </i>
            <i class="fa-regular" 
            style="color: #eeeeec; 
                  position: absolute; 
                  rotate: 30deg;
                  top: 120px; 
                  left: 35px;
                  font-size: 1.5em;">&#x2a;
            </i>
            <i class="fa-regular" 
            style="color: #a9cbfe; 
                  position: absolute; 
                  rotate: 30deg;
                  top: 10px; 
                  left: 105px;
                  font-size: 1.5em;">&#x2a;
            </i>
            <div 
              style="
              position:absolute; 
              top: 40px;
              left: 25px;
              "> 
                <p style=
                  "color:#eeeeec;
                  font-weight: bold;
                  font-family: Times New Roman;
                  font-size:medium;">
                  You met...</p></div>
          </div>
          <div v-else-if="cardType === 4" class="card-type-4-front">
            <span style = "display: inline-block;
                  transform: scaleX(0.5);">            
               <i class="fa-solid" 
               style="color: #599afd; 
                      position: absolute;
                      rotate: 10deg;
                      top: -20px; 
                      left: -12px;
                      font-size: 11.5em;
                      ">&#xf004;
            </i></span>
            <span style = "display: inline-block;
                  transform: scaleX(1.2);">           
               <i class="fa-solid" 
               style="color: #599afd; 
                      position: absolute;
                      rotate: 15deg;
                      top: 60px; 
                      left: 20px;
                      font-size: 5em;
                      ">&#xf004;
            </i> </span>
            <span style = "display: inline-block;
                  transform: scaleX(0.5);">            
               <i class="fa-solid" 
               style="color: #bad5fe; 
                      position: absolute;
                      rotate: 15deg;
                      top: 90px; 
                      left: 130px;
                      font-size: 6em;
                      ">&#xf004;
            </i></span>
            <span style = "display: inline-block;
                  transform: scaleX(0.4);">            
               <i class="fa-regular" 
               style="color: #024ec1; 
                      position: absolute;
                      rotate: 15deg;
                      top: 60px; 
                      left: -10px;
                      font-size: 6em;
                      ">&#xf004;
            </i></span>
            <span style = "display: inline-block;
                  transform: scaleX(.6);">           
               <i class="fa-solid" 
               style="color: #bad5fe; 
                      position: absolute;
                      rotate: 15deg;
                      top: -15px; 
                      left: 0px;
                      font-size: 2em;
                      ">&#xf004;
            </i> </span>
            <span style = "display: inline-block;
                  transform: scaleX(.6);">           
               <i class="fa-regular" 
               style="color: #eeeeec; 
                      position: absolute;
                      rotate: 15deg;
                      top: -15px; 
                      left: 0px;
                      font-size: 2em;
                      ">&#xf004;
            </i> </span>
            <img src="./icons/spiral(5).png" 
                 style=" 
                      position: absolute; 
                      rotate: 240deg;
                      width: 45px;
                      top: 110px; 
                      left: 0px;">
            <img src="./icons/spiral(5).png" 
                 style=" 
                      position: absolute; 
                      rotate: 80deg;
                      width: 60px;
                      top: 3px; 
                      left: 83px;">
            <img src="./icons/spiral(5).png" 
                 style=" 
                      position: absolute; 
                      rotate: 70deg;
                      width: 65px;
                      top: 145px; 
                      left: 75px;">
              <div 
              style="
              position:absolute; 
              top: 40px;
              left: 25px;
              "> 
                <p style=
                  "color:#eeeeec;
                  font-weight: bold;
                  font-family: Times New Roman;
                  font-size:small;">
                  His best quality<br>is...</p></div>
          </div>
          
        </div>
        <div class="card__face card__face--back">
          <div v-if="cardType === 1" class="card-type-1-back">
          </div>
          <div v-else-if="cardType === 2" class="card-type-2-back">
          </div>
          <div v-else-if="cardType === 3" class="card-type-3-back">
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
  background-color: #a8dd9d;
  width: 100%;
  height: 100%;
}

.card-type-3-front {
  background-color: #277dfe;
  width: 100%;
  height: 100%;
}

.card-type-4-front {
  background-color: #a1c6fe;
  width: 100%;
  height: 100%;
}

.card-type-1-back {

}

.card-type-2-back {
  background-color: #a8dd9d;
  width: 100%;
  height: 100%;
}

.card-type-3-back {
  background-color: #277dfe;
  width: 100%;
  height: 100%;
}

.card-type-4-back {
  background-color: #a1c6fe;
  width: 100%;
  height: 100%;
}



</style>

<!-- <a href="https://www.flaticon.com/free-icons/spiral" title="spiral icons">Spiral icons created by Smashicons - Flaticon</a> -->
<!-- <a href="https://www.flaticon.com/free-icons/spiral" title="spiral icons">Spiral icons created by BomSymbols - Flaticon</a> -->
<!-- <a href="https://www.flaticon.com/free-icons/star" title="star icons">Star icons created by Pixel perfect - Flaticon</a> -->