<script setup>
import { watch } from 'vue'

const props = defineProps({
    show: Boolean
})

const emit = defineEmits(['close'])

watch(
    () => props.show,
    (show) => {
        if (show) {
            document.body.style.display = 'block'
        } else {
            document.body.style.display = 'hidden'
        }
    }
)

const close = () => {
    emit('close')
}
</script>

<template>
    <div class="popup" @click.self="close">
        <div class="popup__content">
            <slot></slot>
        </div>
    </div>
</template>

<style scope lang="scss">
.popup {
    position: fixed;
    top: 0;
    left: 0;

    width: 100dvw;
    height: 100dvh;

    background-color: $bg-overlay;

    &__content {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);

        background-color: $bg-canvas;

        width: 100%;
        max-width: 500px;

        border-radius: $border-radius-m;

        padding: 30px 20px;
    }
}
</style>
