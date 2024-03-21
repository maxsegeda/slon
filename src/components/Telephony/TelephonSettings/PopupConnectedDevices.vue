<template>
  <div class="popUpTelephonSettings" v-if="popupTabNamesVisible">
    <div class="divPopupTabNames">
      <h3 class="titlePopupTabNames">НАЙМЕНУВАННЯ ВКЛАДОК</h3>
      <button class="buttonClosePopupTabNames" @click="closePopupTabNames">
        <img src="../assets/close.svg" alt="Закрити" class="imgPopupTabNames" />
      </button>
    </div>
    <button class="futerButtonPopupTabNames">
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
    };
  },
  methods: {
    closePopupTabNames() {
      this.popupTabNamesVisible = !this.popupTabNamesVisible;
    },
    modalClosed() {
      this.popupTabNamesVisible = false;
    },
  },
};
</script>
<style>
.popUpTelephonSettings {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-shadow: 0px 4px 4px 0px #c0c0c0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}

.divPopupTabNames {
  width: 439px;
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
.ulPopupTabNames {
  list-style-type: none;
  width: 439px;
  background-color: #ffffff;
  margin: 0;
  padding: 0;
  padding-top: 21px;
  padding-bottom: 18px;
}
.liPopupTabNames {
  width: 399px;
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

.inputPopupTabNames {
  border: none;
  border-bottom: 2px solid #5c5c5c;
  width: 399px;
  padding-top: 3px;
  padding-bottom: 7px;
  font-weight: 400;
  font-size: 20px;
  line-height: 25px;
  letter-spacing: 0.25px;
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
.futerButtonPopupTabNames {
  display: flex;
  width: 439px;
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
