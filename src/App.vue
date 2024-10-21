<script setup>
import Form from '@/components/Form.vue'
import Sign from '@/components/Sign.vue'
import {onMounted, reactive, useTemplateRef, isProxy,toRaw } from 'vue'




let formData = reactive({
    name: '',
    position: '',
    department: '',
    office_phone_number:'',
    personal_phone_number: '',
    address: ''
});

const sign = useTemplateRef("sign")

async function handleCopy () {
    navigator.clipboard.writeText(sign.value.innerHTML)
}



onMounted(async () => {
    try{
        const res = await fetch(import.meta.env.VITE_API_ENDPOINT)
        const responseData = await res.json();
        formData.name = responseData.name
        formData.position = responseData.position
        formData.department = responseData.department
        formData.office_phone_number = responseData.office_phone_number
        formData.personal_phone_number = responseData.personal_phone_number
        formData.address = responseData.address
        
    } catch (error) {
        console.error(error)
    }
})


</script>

<template>
    
  <div class="wrapper">
    
    <div class="form__wrapper">
        <Form @copy="handleCopy" :data="formData"/>
    </div>
    <Sign ref="sign" :data="formData"/>
  </div>
</template>

<style scoped>

</style>
