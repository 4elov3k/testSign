<script setup>
import { ref } from 'vue';
import Image from "@/components/Image.vue"

const sign = ref(null)
const props = defineProps({
  data: {
    type: Object,
    required: true
  }
});
let data = props.data


defineExpose(sign)
</script>

<template>
<div ref="sign" class="sign">
    <div class="sign__top">
      <div class="sign__elem"><em>С уважением</em></div>
      <div class="sign__elem"><b>{{ data.name }}</b></div>
      <div class="sign__elem"><em>{{ data.position }}</em></div>
      <div class="sign__elem"><em>{{ data.department }}</em></div>
    </div> 
    <div class="sign__bottom">
      <div class="sign__elem"><em v-if="data.office_phone_number">Раб.тел.:{{ data.office_phone_number }}</em></div>
      <div class="sign__elem"><em v-if="data.personal_phone_number">Моб.тел.:{{ data.personal_phone_number }}</em></div>
      <div class="sign__elem"><em>{{ data.address }}</em></div>
      <div class="sign__elem"><a href="https://www.google.ru/"><Image/></a></div>
    </div>
</div>

</template>

