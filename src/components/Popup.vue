<script setup>
import { watch } from 'vue'

const props = defineProps({
    show: Boolean
})

const emit = defineEmits(['update:show'])

watch(
    () => props.show,
    (show) => {
        if (show) {
            document.body.style.overflow = 'hidden'
        } else {
            document.body.style.overflow = 'auto'
        }
    }
)
</script>

<template>
    <div v-if="show" class="popup" @click.self="$emit('update:show', false)">
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
