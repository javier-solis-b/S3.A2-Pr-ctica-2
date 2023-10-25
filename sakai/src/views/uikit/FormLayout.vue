<script setup>
import { ref } from 'vue';
import Button from 'primevue/button';

const dropdownItems = ref([
    { name: 'Option 1', code: 'Option 1' },
    { name: 'Option 2', code: 'Option 2' },
    { name: 'Option 3', code: 'Option 3' }
]);

const dropdownItem = ref(null);

const calendarValue = ref(null);
</script>

<template>
    <div class="grid">
        <div class="col-12 md:col-12">
            <div class="card p-fluid">
                <h5>GENERAR EL RFC DE UNA PERSONA</h5>
                <div class="field">
                    <label for="name1">Nombre(s):</label>
                    <InputText id="name1" type="text" />
                </div>
                <div class="field">
                    <label for="ape1">Apellido Paterno:</label>
                    <InputText id="ape1" type="text" />
                </div>
                <div class="field">
                    <label for="ape2">Apellido Materno:</label>
                    <InputText id="ape2" type="text" />
                </div>
                <div class="field">
                    <label for="calendar">Fecha:</label>
                    <Calendar :showIcon="true" :showButtonBar="true" v-model="calendarValue"></Calendar>
                </div>
                <div class="field">
                    <label for="rfc">RFC:</label>
                    <InputText id="rfc" type="text" />
                </div>
                <div class="col-6 md:col-7">
                    <Button label="GENERAR" />
                </div>
            </div>
            
        </div>
       
      
    </div>
</template>
