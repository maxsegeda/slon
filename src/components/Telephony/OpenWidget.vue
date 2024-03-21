<template>
  <div class="divOpenWidget">
    <h3 class="h3OpenWidget">{{ newLatestInteractions }}</h3>
    <button class="buttonOpenWidget">
      <img
        src="../Telephony/assets/open.svg"
        alt="Відкрити"
        class="imgOpenWidget"
      />
    </button>
  </div>
  <div class="divOpenWidget">
    <h3 class="h3OpenWidget">ПРОПУЩЕНІ ДЗВІНКИ</h3>
    <button class="buttonOpenWidget">
      <img
        src="../Telephony/assets/open.svg"
        alt="Відкрити"
        class="imgOpenWidget"
      />
    </button>
  </div>
  <div class="divOpenWidget">
    <h3 class="h3OpenWidget">ІСТОРІЯ ДЗВІНКІВ</h3>
    <button class="buttonOpenWidget">
      <img
        @click="historyCalls"
        src="../Telephony/assets/open.svg"
        alt="Відкрити"
        class="imgOpenWidget"
        :style="{ transform: openHistoryCalls ? 'rotate(180deg)' : 'none' }"
      />
    </button>
  </div>
  <CallHistory v-if="openHistoryCalls" />
  <PopupTabNames
    @update:latestInteractions="updatelatestInteractions"
    class="popupTabNames"
  />
</template>
<script>
import CallHistory from "./CallHistory.vue";
import PopupTabNames from "./TelephonSettings/PopupTabNames.vue";
export default {
  components: {
    CallHistory,
    PopupTabNames,
  },
  data() {
    return {
      openHistoryCalls: false,
      newLatestInteractions: "ОСТАННІ ВЗАЄМОДІЇ",
    };
  },
  methods: {
    historyCalls() {
      this.openHistoryCalls = !this.openHistoryCalls;
    },
    updatelatestInteractions(latestInteractions) {
      this.newLatestInteractions = latestInteractions;
    },
  },
};
</script>
<style>
.divOpenWidget {
  width: 451px;
  height: 70px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: white;
  box-shadow: 0px 4px 4px 0px #c0c0c0;
  border-bottom: 1px solid #c0c0c0;
}
.h3OpenWidget {
  margin-left: 16px;
  font-family: Roboto Condensed;
  font-size: 20px;
  font-weight: 400;
  line-height: 25px;
  letter-spacing: 0.25px;
  text-align: left;
}
.buttonOpenWidget {
  margin-right: 16px;
  border: none;
  background-color: white;
  cursor: pointer;
}
.imgOpenWidget {
  width: 24px;
  height: 14.84px;
}
</style>
