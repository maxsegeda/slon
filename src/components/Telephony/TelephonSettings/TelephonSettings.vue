<template>
  <div class="telephonSettings">
    <button class="settings" @click="openConnectedDevices">
      <img
        src="../assets/connectedDevices.svg"
        alt="ПРИЄДНАНІ ПРИСТРОЇ"
        class=""
      />
      <h3>ПРИЄДНАНІ ПРИСТРОЇ</h3>
    </button>
    <button class="settings" @click="openTabNames">
      <img src="../assets/tabNames.svg" alt="НАЙМЕНУВАННЯ ВКЛАДОК" class="" />
      <h3>НАЙМЕНУВАННЯ ВКЛАДОК</h3>
    </button>
    <button class="settings" @click="openPeriodsAndIntervals">
      <img
        src="../assets/periodsAndIntervals.svg"
        alt="ПЕРІОДИ ТА ІНТЕРВАЛИ"
        class=""
      />
      <h3>ПЕРІОДИ ТА ІНТЕРВАЛИ</h3>
    </button>
  </div>
  <PopupConnectedDevices
    @click.self="closeConnectedDevices"
    v-if="popupConnectedDevices"
    class="popupConnectedDevices"
  />

  <PopupPeriodsAndIntervals
    @click.self="closePeriodsAndIntervals"
    v-if="popupPeriodsAndIntervals"
    class="popupPeriodsAndIntervals"
  />
</template>

<script>
import PopupPeriodsAndIntervals from "./PopupPeriodsAndIntervals.vue";
import PopupConnectedDevices from "./PopupConnectedDevices.vue";

export default {
  components: {
    PopupConnectedDevices,
    PopupPeriodsAndIntervals,
  },
  name: "TelephonSettings",

  data() {
    return {
      popupConnectedDevices: false,
      popupTabNames: false,
      popupPeriodsAndIntervals: false,
    };
  },
  methods: {
    openConnectedDevices() {
      this.popupConnectedDevices = !this.popupConnectedDevices;
    },
    closeConnectedDevices() {
      this.popupConnectedDevices = false;
    },
    openTabNames() {
      this.popupTabNames = !this.popupTabNames;
      this.$emit("update:popupTabNames", this.popupTabNames);
    },
    closeTabNames() {
      this.popupTabNames = false;
    },
    openPeriodsAndIntervals() {
      this.popupPeriodsAndIntervals = !this.popupPeriodsAndIntervals;
    },
    closePeriodsAndIntervals() {
      this.popupPeriodsAndIntervals = false;
    },
  },
};
</script>

<style>
template {
  position: relative;
}
.telephonSettings {
  display: grid;
  width: 389px;
  height: 171px;
  box-shadow: 0px 4px 4px 0px #c0c0c0;
  background-color: white;
}
.settings {
  padding-left: 26px;
  height: 57px;
  width: 100%;
  display: flex;
  background-color: white;
  border: 1px solid white;
  border-bottom: 1px solid #c0c0c0;
  cursor: pointer;
}
img {
  width: 48px;
  height: 48px;
  margin-right: 8px;
}
h3 {
  font-size: 18px;
  font-weight: 400;
  line-height: 25px;
  color: #666666;
  margin: auto 0;
}
.popupTabNamesVisible {
  width: 300px;
  height: 300px;
  background-color: black;
}
</style>
