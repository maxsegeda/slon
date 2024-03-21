<template>
  <div class="telephonyWidget">
    <div class="conteinerTelephonyWidget">
      <button
        @click="openWidget"
        class="buttonTelephonyWidget"
        :style="{
          boxShadow: isOpenWidget
            ? '0px 4px 4px 0px transparent'
            : '0px 4px 4px 0px #c0c0c0',
        }"
      >
        <div class="icon-text-container">
          <img
            src="./assets/telephon.svg"
            alt="ТЕЛЕФОНІЯ"
            class="telephony-telephonSettings-icon"
          />
          <span class="text-container">{{ nameWidget }}</span>
          <span
            class="missed-cals"
            :style="{
              backgroundColor: missedCallsCount === 0 ? '#666666' : '#ff6633',
            }"
            >{{ missedCallsCount }}
          </span>
        </div>
        <button
          @click="imgSettings"
          class="ButtonTelephonyTelephonSettings"
          :style="{ display: isSettingsVisible ? 'block' : '' }"
        >
          <img
            src="./assets/telephonSettings.svg"
            alt="НАЛАШТУВАННЯ"
            class="telephony-telephonSettings-icon"
          />
        </button>
      </button>
      <TelephonSettings
        @click.self="closeSettingsPopup"
        v-if="isSettingsVisible"
        @update:popupTabNames="closeWidgetName"
      />
    </div>
    <PopupTabNames
      v-if="newTabNamesState"
      @update:newNameWidget="updateWidgetName"
      class="popupTabNames"
    />
    <OpenWidget v-if="isOpenWidget" class="openWidget" />
  </div>
</template>

<script>
import TelephonSettings from "./TelephonSettings/TelephonSettings.vue";
import OpenWidget from "./OpenWidget.vue";
import PopupTabNames from "./TelephonSettings/PopupTabNames.vue";
export default {
  components: {
    TelephonSettings,
    OpenWidget,
    PopupTabNames,
  },
  data() {
    return {
      missedCallsCount: 4,
      isOpenWidget: false,
      isSettingsVisible: false,
      nameWidget: "ТЕЛЕФОНІЯ",
      newTabNamesState: "",
    };
  },

  methods: {
    openWidget() {
      this.isOpenWidget = !this.isOpenWidget;
    },
    imgSettings() {
      this.isSettingsVisible = !this.isSettingsVisible;
      this.isOpenWidget = !this.isOpenWidget;
    },
    closeSettingsPopup() {
      this.isSettingsVisible = false;
    },
    closeWidgetName(popupTabNames) {
      this.newTabNamesState = popupTabNames;
    },
    updateWidgetName(newNameWidge) {
      this.nameWidget = newNameWidge;
    },
  },
};
</script>

<style>
.telephonyWidget {
  display: flex;
  flex-direction: column;
}
.conteinerTelephonyWidget {
  display: flex;
}
.buttonTelephonyWidget {
  width: 451px;
  height: 70px;
  border: none;
  background: #ffffff;
  border-bottom: 1px solid #c4c4c4;
  box-shadow: 0px 4px 4px 0px #c0c0c0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0;
}
.telephony-widget:hover {
  box-shadow: 0px 4px 4px 0px #696969;
  cursor: pointer;
}
.icon-text-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.telephony-telephonSettings-icon {
  width: 36px;
  height: 36px;
  margin: 0 22px;
}
.text-container {
  font-size: 24px;
  font-weight: 400;
  line-height: 36px;
  color: #666665;
}
.missed-cals {
  width: 36px;
  height: 36px;
  margin: 0 8px;
  border-radius: 50%;
  font-size: 24px;
  font-weight: 400;
  line-height: 36px;
  color: white;
}
.ButtonTelephonyTelephonSettings {
  border: none;
  background-color: white;
  cursor: pointer;
  display: none;
}
.conteinerTelephonyWidget:hover .ButtonTelephonyTelephonSettings {
  display: block;
}

.popupTabNames {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
