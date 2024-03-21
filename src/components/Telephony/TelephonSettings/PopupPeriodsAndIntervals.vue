<template>
  <div class="popUpPeriodsAndIntervals" v-if="popupTabNamesVisible">
    <div class="divPopupPeriodsAndIntervals">
      <h3 class="titlePopupTabNames">ПЕРІОДИ ТА ІНТЕРВАЛИ</h3>
      <button class="buttonClosePopupTabNames" @click="closePopupTabNames">
        <img src="../assets/close.svg" alt="Закрити" class="imgPopupTabNames" />
      </button>
    </div>
    <ul class="ulPopupPeriodsAndIntervals">
      <li class="liPopupPeriodsAndIntervals">
        <h5 class="h5PopupTabNames">
          ПЕРІОД СЛІДКУВАННЯ ЗА ОСТАННІМИ ВЗАЄМОДІЯМИ
        </h5>
        <div class="divInputPopupTabNames">
          <input
            type="text"
            placeholder="1сек"
            class="inputPopupPeriodsAndInterval"
            ref="inputCounter"
            v-model="counterValueRecentInteractions"
          />

          <div class="divImgPopupTabNames">
            <button class="buttonPlusMinus">
              <img
                @click="counterPlusRecentInteractions"
                src="../assets/plus.svg"
                alt="plus"
                class="imgPlusMinus"
              />
            </button>
            <button class="buttonPlusMinus">
              <img
                @click="counterMinusRecentInteractions"
                src="../assets/minus.svg"
                alt="minus"
                class="imgPlusMinus"
              />
            </button>
          </div>
        </div>
        <p class="pPopupTabNames">оберіть 1-120 сек.</p>
      </li>
      <li class="liPopupPeriodsAndIntervals">
        <h5 class="h5PopupTabNames">
          ПЕРІОД СЛІДКУВАННЯ ЗА ПРОПУЩЕНИМИ ДЗВІНКАМИ
        </h5>
        <div class="divInputPopupTabNames">
          <input
            type="text"
            placeholder="1сек"
            class="inputPopupPeriodsAndInterval"
            ref="inputCounter"
            v-model="counterValueMissedCalls"
          />

          <div class="divImgPopupTabNames">
            <button class="buttonPlusMinus">
              <img
                @click="counterPlusMissedCalls"
                src="../assets/plus.svg"
                alt="plus"
                class="imgPlusMinus"
              />
            </button>
            <button class="buttonPlusMinus">
              <img
                @click="counterMinusMissedCalls"
                src="../assets/minus.svg"
                alt="minus"
                class="imgPlusMinus"
              />
            </button>
          </div>
        </div>
        <p class="pPopupTabNames">оберіть 1-24год.</p>
      </li>
      <li class="liPopupPeriodsAndIntervals">
        <h5 class="h5PopupTabNames">ІНТЕРВАЛ ОБ’ЄДНАННЯ ПРОПУЩЕНИХ ДЗВІНКІВ</h5>
        <div class="divInputPopupTabNames">
          <input
            type="text"
            placeholder="1сек"
            class="inputPopupPeriodsAndInterval"
            ref="inputCounter"
            v-model="counterValueInterval"
          />

          <div class="divImgPopupTabNames">
            <button class="buttonPlusMinus">
              <img
                @click="counterPlusInterval"
                src="../assets/plus.svg"
                alt="plus"
                class="imgPlusMinus"
              />
            </button>
            <button class="buttonPlusMinus">
              <img
                @click="counterMinusInterval"
                src="../assets/minus.svg"
                alt="minus"
                class="imgPlusMinus"
              />
            </button>
          </div>
        </div>
        <p class="pPopupTabNames">оберіть 0-60сек.</p>
      </li>
    </ul>
    <button class="futerPopupPeriodsAndIntervals">
      <img src="../assets/savePopUp.svg" alt="Зберегти" class="" />
      <h3>ЗБЕРЕГТИ</h3>
    </button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      popupTabNamesVisible: true,
      counterValueRecentInteractions: 0,
      counterValueMissedCalls: 0,
      counterValueInterval: 0,
    };
  },
  methods: {
    closePopupTabNames() {
      this.popupTabNamesVisible = !this.popupTabNamesVisible;
    },
    modalClosed() {
      this.popupTabNamesVisible = false;
    },
    counterPlusRecentInteractions() {
      this.counterValueRecentInteractions++;
    },
    counterMinusRecentInteractions() {
      this.counterValueRecentInteractions = Math.max(
        this.counterValueRecentInteractions - 1,
        0
      );
    },
    counterPlusMissedCalls() {
      this.counterValueMissedCalls++;
    },
    counterMinusMissedCalls() {
      this.counterValueMissedCalls = Math.max(
        this.counterValueMissedCalls - 1,
        0
      );
    },
    counterPlusInterval() {
      this.counterValueInterval++;
    },
    counterMinusInterval() {
      this.counterValueInterval = Math.max(this.counterValueInterval - 1, 0);
    },
  },
};
</script>
<style>
.popUpPeriodsAndIntervals {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-shadow: 0px 4px 4px 0px #c0c0c0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}

.divPopupPeriodsAndIntervals {
  width: 487px;
  height: 54px;
  background-color: #659cc1;
  display: flex;
  justify-content: space-between;
}
.titlePopupTabNames {
  font-size: 24px;
  font-weight: 400;
  line-height: 36px;
  color: #ffffff;
  margin-left: 20px;
}
.buttonClosePopupTabNames {
  border: none;
  background-color: #659cc1;
  cursor: pointer;
}
.imgPopupTabNames {
  width: 36px;
  height: 36px;
  color: white;
}
.ulPopupPeriodsAndIntervals {
  width: 487px;
  background-color: white;
  margin: 0;
  padding: 0;
  padding-top: 21px;
  padding-bottom: 18px;
}
.liPopupPeriodsAndIntervals {
  list-style-type: none;
  width: 447px;
  height: 69px;
  background-color: #ffffff;
  margin-left: 20px;
  padding-bottom: 14px;
}
.h5PopupTabNames {
  color: #999999;
  font-size: 15px;
  font-weight: 400;
  line-height: 20px;
  text-align: left;
  margin: 0;
}
.divInputPopupTabNames {
  border-bottom: 2px solid #5c5c5c;
  display: flex;
  align-items: center;
  justify-content: center;
}
.divImgPopupTabNames {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.buttonPlusMinus {
  all: unset;
  border: none;
  background-color: transparent;
  margin: -4px 0;
  padding: 0;
  cursor: pointer;
}
.imgPlusMinus {
  width: 12px;
  height: 6px;
  margin: 0;
  padding: 0;
  border: none;
}

.inputPopupPeriodsAndInterval {
  border: none;
  width: 447px;
  padding-top: 3px;
  font-weight: 400;
  font-size: 20px;
  line-height: 25px;
  letter-spacing: 0.25px;
  color: #5c5c5c;
}
.inputPopupPeriodsAndInterval::placeholder {
  font-weight: 400;
  font-size: 20px;
  line-height: 25px;
  letter-spacing: 0.25px;
  color: #999999;
}
.pPopupTabNames {
  font-family: "Roboto Condensed";
  font-size: 12px;
  font-weight: 400;
  line-height: 14px;
  letter-spacing: 0px;
  text-align: left;
  color: red;
  margin-top: 0;
}
.futerPopupPeriodsAndIntervals {
  display: flex;
  width: 487px;
  height: 65px;
  align-items: center;
  justify-content: center;
  border: none;
  background-color: #e5e5e5;
  cursor: pointer;
}
.futerButtonPopupTabNames img {
  width: 35x;
  height: 27px;
  margin: 0;
}
.futerButtonPopupTabNames h3 {
  font-size: 24px;
  font-weight: 400;
  line-height: 36px;
}
</style>
