<template>
  <StreamBarcodeReader @decode="onDecode" @loaded="onLoaded"></StreamBarcodeReader>
  <!-- <StreamBarcodeReader @decode="onDecode" :busy="data.isAdding" @loaded="onLoaded"></StreamBarcodeReader> -->
  <!-- <QuoggaReader @onDetected="onDecode" /> -->
  <textarea>{{ data.barcodeText }}s</textarea>
</template>
<script setup>
import { ref, reactive } from "vue";
import StreamBarcodeReader from "./components/StreamBarcodeReader.vue";
import QuoggaReader from "./components/QuoggaReader.vue";
const data = reactive({ loading: true, isAdding: false, barcodeText: null });

const onLoaded = () => {
  data.loading = false;
  alert("loaded new 3");
};

const onDecode = async (text) => {
  data.barcodeText = text;
  alert("text.codeResult", text);
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
