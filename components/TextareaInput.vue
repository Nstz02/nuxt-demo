<template>
    <textarea
        class="appearance-none block w-full bg-gray-200 text-gray-700 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white"
        rows="3" 
        placeholder="ที่อยู่"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"></textarea>
</template>

<script setup>
defineProps({
    modelValue: {
        type: String,
        default: "",
    }
});
</script>

<style scoped></style>