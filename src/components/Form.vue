<script setup>
import {vMaska} from "maska/vue"


const props = defineProps({
    data:{
        type: Object,
        required: true
    }
    
})
const emit = defineEmits(["copy"])
let data = props.data
function copyToText (){
    const text = `
    ${data.name}
    ${data.position}
    ${data.department}
    Раб.тел.:${data.office_phone_number}
    Моб.тел.:${data.personal_phone_number}
    ${data.address}
`;
    navigator.clipboard.writeText(text)

}
function copyToHTML (){
    emit("copy")
}

</script>

<template>
    <form action="" class="form">
        <div class="form__item"><label for="name">Фамилия Имя</label>
        <input v-model="data.name" id="name" maxlength="48" type="text"></div>

        <div class="form__item">
            <label for="position">Должность</label>
            <input maxlength="64" v-model="data.position" id="position" type="text">
        </div>

        <div class="form__item">
            <label for="department">Подразделение</label>
            <input maxlength="64" v-model="data.department" id="department" type="text">
        </div>

        <div class="form__item">
            <label for="office_phone_number">Рабочий телефон</label>
            <input v-maska="'+7(###)-###-##-##, (###)-####'" v-model="data.office_phone_number" id="office_phone_number" type="tel">
        </div>

        <div class="form__item">
            <label for="personal_phone_number">Мобильный телефон</label>
            <input v-maska="'+7(###)-###-##-##'" v-model="data.personal_phone_number" id="personal_phone_number" >
        </div>

        <div class="form__item">
            <label for="address">Местоположение</label>
            <input maxlength="64" v-model="data.address" id="address" type="text">
        </div>

        
    </form>
    <div class="buttons-set">
            <div class="buttons-set__item">
                <span>Копировать текст подписи</span>
                <button type="button" @click="copyToText">Копировать текстом</button>
            </div>

            <div class="buttons-set__item">
                <span>Копировать кодом для вставки</span>
                <button type="button" @click="copyToHTML">Копировать кодом</button>
            </div>
    </div>
</template>

<style scoped>
</style>
