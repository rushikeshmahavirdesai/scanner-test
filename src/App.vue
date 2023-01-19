<template>
  <QuoggaReader @onDetected="onDecode" />
  <!-- <StreamBarcodeReader v-if="cart.mobileScanner" :busy="data.isAdding" @decode="onDecode" @loaded="onLoaded"></StreamBarcodeReader> -->
</template>

<script setup>
import { ref, reactive } from "vue";
import StreamBarcodeReader from "./components/StreamBarcodeReader.vue";
import QuoggaReader from "./components/QuoggaReader.vue";

const data = reactive({ loading: true, isAdding: false });
const audio = new Audio("/beep.mp3");

const onLoaded = () => (data.loading = false);

const onDecode = async (text) => {
  if (data.isAdding) return false;
  alert("text.codeResult.code", text.codeResult.code);
  text.codeResult.code;
  data.isAdding = true;

  data.isAdding = false;
};
</script>

<style scoped>
.information {
  margin-top: 100px;
}
</style>
