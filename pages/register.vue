<template>
  <form @submit.prevent="submitForm">
    <div class="antialiased text-gray-900 px-6">
      <h2 class="text-2xl font-bold text-center">Registration</h2>
      <div class="max-w-xl mx-auto py-12 md:max-w-4xl">
        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                Full Name
              </label>
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 text-center">
                <div class="appearance-none block w-full bg-gray-200 text-gray-700 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white">
                  {{ fullName }}
                </div>
              </label>
        <div class="mt-8 grid grid-cols-1 md:grid-cols-2 gap-6 items-start">
          <div class="grid grid-cols-1 gap-6">
            <label class="block">
              <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                First Name
              </label>
              <TextBoxInput v-model="formData.firstname" placeholder="ชื่อ" />
            </label>
          </div>
          <div class="grid grid-cols-1 gap-6">
            <label class="block">
              <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                Last Name
              </label>
              <TextBoxInput v-model="formData.lastname" placeholder="นามสกุล" />
            </label>
          </div>
        </div>
        <div class="mt-8 grid grid-cols-1 md:grid-cols-1 gap-6 items-start">
          <div class="grid grid-cols-1 gap-6">
            <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
              <span class="text-gray-700">Date of Birth</span>
              <Calendar v-model="formData.birthday" id="birthday" />
            </label>
            <fieldset class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
              <legend class="text-gray-700">Gender</legend>
              <div class="mt-2">
                <div>
                  <label class="inline-flex items-center">
                    <RadioButton name="radio-sex" value="Male" v-model="formData.sex" />
                    <span class="ml-2">Male</span>
                  </label>
                </div>
                <div>
                  <label class="inline-flex items-center">
                    <RadioButton name="radio-sex" value="Female" v-model="formData.sex" />
                    <span class="ml-2">Female</span>
                  </label>
                </div>
              </div>
            </fieldset>
            <fieldset class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
              <legend class="text-gray-700">Hobbies</legend>
              <div class="mt-2">
                <div>
                  <label class="inline-flex items-center">
                    <CheckBox value="Sport" v-model="formData.hobbies"/>
                    <span class="ml-2">Sport</span>
                  </label>
                </div>
                <div>
                  <label class="inline-flex items-center">
                    <CheckBox value="Book" v-model="formData.hobbies"/>
                    <span class="ml-2">Book</span>
                  </label>
                </div>
                <div>
                  <label class="inline-flex items-center">
                    <CheckBox value="Movie" v-model="formData.hobbies"/>
                    <span class="ml-2">Movie</span>
                  </label>
                </div>
                <div>
                  <label class="inline-flex items-center">
                    <CheckBox value="Sleep" v-model="formData.hobbies"/>
                    <span class="ml-2">Sleep</span>
                  </label>
                </div>
              </div>
            </fieldset>

            <label class="block">
              <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                Address
              </label>
              <TextareaInput v-model="formData.address" placeholder="ที่อยู่" />
            </label>
            <label class="block">
              <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                Email
              </label>
              <TextBoxInput v-model="formData.email" placeholder="hello_note@example.com" />
            </label>
            <label class="block">
              <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                Phone Number
              </label>
              <TextBoxInput v-model="formData.phone" placeholder="0982868752" />
            </label>
            <label class="block">
              <div class="container py-10 px-10 mx-0 min-w-full flex flex-col items-center">
                <ButtonSubmit />
              </div>
            </label>
          </div>
        </div>
      </div>
    </div>
  </form>
</template>

<script setup lang="ts">

import { ref } from 'vue';

const formData = ref(
  {
    firstname: '',
    lastname: '',
    birthday: '',
    sex: 'Male',
    address: '',
    email: '',
    phone: '',
    hobbies: [] as string[]
  })

const fullName = computed(() => [formData.value.firstname, formData.value.lastname].filter((x) => x!!).join(' '))

const submitForm = async () => {

  const { data: resData } = await useFetch('http://localhost:59737/api/customers/demo/register', {
    method: 'post',
    body: {
      firstname: formData.value.firstname,
      lastname: formData.value.lastname,
      birthday: formData.value.birthday,
      sex: formData.value.sex,
      address: formData.value.address,
      email: formData.value.email,
      phone: formData.value.phone,
      hobbies: formData.value.hobbies
    }
  })

  console.log(resData)

}

</script>

<style scoped></style>