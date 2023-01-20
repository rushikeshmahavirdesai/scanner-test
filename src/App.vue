<template>
  <StreamBarcodeReader @decode="onDecode" @loaded="onLoaded"></StreamBarcodeReader>
  <!-- <StreamBarcodeReader @decode="onDecode" :busy="data.isAdding" @loaded="onLoaded"></StreamBarcodeReader> -->
  <!-- <QuoggaReader @onDetected="onDecode" /> -->
  <h2>The decoded value in QR/barcode is</h2>
</template>
<script setup>
import { ref, reactive } from "vue";
import StreamBarcodeReader from "./components/StreamBarcodeReader.vue";
import QuoggaReader from "./components/QuoggaReader.vue";
const data = reactive({ loading: true, isAdding: false });

const onLoaded = () => {
  data.loading = false;
  alert("loaded new 3");
};

const onDecode = async (text) => {
  alert("text.codeResult", text.codeResult.code);
};
</script>

<style scoped>
a {
  color: #42b983;
}
.information {
  margin-top: 100px;
}
</style>
