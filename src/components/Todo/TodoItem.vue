<template>
    <div class="flex items-center justify-between bg-white rounded-xl px-4 py-3 shadow-lg">
        <div class="flex-1 min-w-0 pr-3">
          <!--Tampilan normal-->
          <span v-if="!isEditing">{{ todo.text }}</span>

          <!--Input Saat edit-->
          <BaseInput 
            v-else
            v-model="editText"
            placeholder="Edit todo"
            @keyup.enter="OnSave"
          />
        </div>

        <div class="flex gap-1 ml-2">
            <!---Tombol saat tidak edit-->
            <template v-if="!isEditing">
                <BaseButton
                    label="Edit"
                    variant="secondary"
                    @click="OnEdit"
                />
                <BaseButton
                    label="Delete"
                    variant="secondary"
                    @click="OnDelete"
                />
            </template>
            <!---Tombol saat edit-->
            <template v-else>
                <BaseButton 
                    label="Save"
                    variant="primary"
                    @click="OnSave"
                />
                <BaseButton 
                    label="Cancel"
                    variant="secondary"
                    @click="OnCancel"
                />
            </template>
        </div>
    </div>
</template>

<script setup>
import {ref} from 'vue';
import BaseButton from '../Base/BaseButton.vue';
import BaseInput from '../Base/BaseInput.vue';

const props = defineProps({
    todo: Object
})

const emit = defineEmits('delete', 'edit', 'save')

const isEditing = ref(false)
const editText = ref ('')

const OnEdit = () => {
    isEditing.value = true
    editText.value = props.todo.text
}

const OnSave = () => {
    emit('save', editText.value)
    isEditing.value = false
}

const OnCancel = () => {
    isEditing.value = false
    editText.value = ''
}

const OnDelete = () => {
    emit('delete')
}
</script>

<style lang="scss" scoped>

</style>