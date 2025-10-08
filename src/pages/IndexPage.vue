<template>
  <q-page class="q-pa-md flex flex-center">
    <q-card style="width: 300px;">
      <q-card-section>
        <div class="text-h6">Name</div>
      </q-card-section>

      <q-card-section>
        <q-form ref="myForm" class="q-gutter-md">

          <q-input
            filled
            v-model="form.name"
            label="Name"
            :rules="[val => !!val || 'Add Name']"
          />

          <div class="row justify-end q-gutter-sm">
            <q-btn label="Submit" color="primary" @click="validate" />
            <q-btn label="Reset" color="primary" flat @click="reset" />
          </div>

        </q-form>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const myForm = ref(null)

const form = ref({
  name: ''
})

function validate () {
  myForm.value.validate().then(success => {
    if (success) {
      alert(`Your Name: ${form.value.name}`)
    } else {
      alert('Valid Name')
    }
  })
}

function reset () {
  myForm.value.resetValidation()
  form.value.name = ''
}
</script>