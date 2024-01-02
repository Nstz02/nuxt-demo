<template>
    <input class="form-radio" 
    type="radio" 
    :value="props.value"
    v-model="model"/>
</template>

<script lang="ts" setup>

const props = withDefaults(
  defineProps<{
    modelValue?: string;
    value: string
  }>(),
  {
    modelValue: () => "",
  },
);

const emit = defineEmits<{
  (e: 'update:modelValue', val: string): void;
}>();

const model = computed({
get(){
     return props.modelValue;
},
set(value: string) {
     emit("update:modelValue", value)
}
});
</script>

<style scoped></style>