<template>
    <input 
        :model-value="modelValue"
        :type="type"
        :placeholder="placeholder"
        class="flex-1 px-4 py-3 bg-white rounded-xl outline-none w-full border 
        border-gray-300"
        @input="onInput"
        @keyup.enter="onEnter"
    >
</template>

<script setup>
defineProps ({
    id: String,
    placeholder: String,
    type: String,
    modelValue: String,
})

const emit = defineEmits(['update:modelValue', 'enter'])

const onEnter = () => {
    emit('enter')
}

const onInput = (event) => {
    emit('update:modelValue', event.target.value)
}
</script>

<style lang="scss" scoped>
    
</style>