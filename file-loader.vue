<template>
    <div ref="container" @click="clickContainer" @dragover="dragoverContainer" @drop="dropContainer">
        <input ref="input" @change="changeInput" @click="clickInput" type="file" style="display:none;"
            :accept="props.accept" :multiple="props.multiple" :capture="props.capture">
        <slot></slot>
    </div>
</template>
<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
    'accept': {
        default: '*'
    },
    'multiple': {
        default: false
    },
    'capture': {
        default: 'user'
    },
    'drag': {
        default: true
    }
})
const emits = defineEmits(['load'])


const files = ref()
watch(files, () => {
    const filesValue = files.value
    filesValue.toFormData = toFormData
    emits['load'](filesValue)
})


const container = ref()
const input = ref()


function clickContainer() {
    input.value.click()
}
function dragoverContainer(e) {
    if (props.drag || props.drag === '') {
        e.preventDefault()
    }
}
function dropContainer(e) {
    e.preventDefault()
    files.value = e.dataTransfer.files
}


function changeInput() {
    files.value = input.value.files
}
function clickInput(e) {
    e.stopPropagation()
}

function toFormData(extraData = {}) {
    const formData = new FormData()
    Array.from(this)?.forEach(file => {
        formData.append(`file${new Date().getTime}`, file)
    })
    Object.keys(extraData).forEach(key => {
        formData.append(key, extraData[key])
    })
    return formData
}
</script>