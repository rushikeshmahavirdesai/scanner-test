<template>
  <!-- <StreamBarcodeReader @decode="onDecode" @loaded="onLoaded"></StreamBarcodeReader> -->
  <StreamBarcodeReader @decode="onDecode" :busy="data.isAdding" @loaded="onLoaded"></StreamBarcodeReader>
  <h2>The decoded value in QR/barcode is</h2>
  <h2>{{ decodedText }}</h2>

  <p class="information">
    <strong>Github:</strong>
    <a href="https://github.com/olefirenko/vue-barcode-reader" target="_blank"> https://github.com/olefirenko/vue-barcode-reader</a>
  </p>
  <p>
    <strong>NPM:</strong>
    <a href="https://www.npmjs.com/package/vue-barcode-reader" target="_blank"> https://www.npmjs.com/package/vue-barcode-reader</a>
  </p>
  <p>
    Check <strong>vue-barcode-reader</strong> library in production at
    <a href="https://parceltrackingapp.com/en" target="_blank">ParcelTrackingApp.com</a>
  </p>
</template>
<script setup>
import { ref, reactive } from "vue";
import StreamBarcodeReader from "./components/StreamBarcodeReader.vue";

const data = reactive({ loading: true, isAdding: false });

const onLoaded = () => {
  data.loading = false;
  alert("loaded new 2");
};

const onDecode = async (text) => {
  if (data.isAdding) return false;
  const product = "ddddd";
  data.isAdding = true;
  if (product) {
    alert("text.codeResult", text.codeResult);
  }
  data.isAdding = false;
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
