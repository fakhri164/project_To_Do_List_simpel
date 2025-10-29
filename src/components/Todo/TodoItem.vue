<template>
    <div class="flex items-center justify-between bg-white rounded-xl px-4 py-3 shadow-lg">
        <div class="flex-1 min-w-0 pr-3">
            {{ todo.text }}
        </div>

        <div class="flex gap-1 ml-2">
            <BaseButton
                label="Delete"
                variant="secondary"
                @click="OnDelete"
            />
        </div>
    </div>
</template>

<script setup>
import BaseButton from '../base/BaseButton.vue';

defineProps({
    todo: Object
})


const emit = defineEmits('delete', 'edit')

const OnDelete = () => {
    emit('delete')
}
</script>

<style lang="scss" scoped>

</style>