<template>
    <button
        :class="defaultClass"
        @click="handleClick"
    >
        {{ label }}
    </button>
</template>

<script setup>
import {computed} from 'vue'

const props = defineProps({
    label: {
        type: String,
        required:true
    },
    variant: {
        type: String,
        default: 'primary'
    },
    customClass: {
        type: String,
        default: ''
    },
    outline: {
        type: Boolean,
        default: false
    }
})

const variantClass = {
    primary: 'bg-slate-700 text-white',
    secondary: 'bg-gray-500 text-gray-500'
}

const outlineClass = {
    primary: 'border-white border text-white',
    secondary: 'border-gray-700 border text-gray-500'
}

const defaultClass = computed(() => {
    const baseClass = 'px-6 py-3 rounded-xl flex items-center cursor-pointer'

    const newClass = props.outline
    ? outlineClass[props.variant]
    :variantClass[props.variant]

    return `${baseClass} ${newClass} ${props.customClass}`
})

const emit = defineEmits(['click'])
const handleClick = () => {
    emit('click')
}
</script>

<style lang="scss" scoped>
    
</style>