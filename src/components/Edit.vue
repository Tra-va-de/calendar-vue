<script setup>
import { ref } from 'vue'

const props = defineProps({
    modelValue: {
        type: [String, Number],
        default: ''
    },
    placeholder: {
        type: String,
        default: ''
    }
})

const focused = ref(false)

const emits = defineEmits(['update:modelValue'])
</script>

<template>
    <div
        class="edit"
        :class="{ filled: modelValue !== null && modelValue !== '', focused: focused }"
    >
        <input
            class="edit__input"
            type="text"
            :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value)"
            @focus="focused = true"
            @blur="focused = false"
        />

        <div class="edit__placeholder">
            {{ placeholder }}
        </div>
    </div>
</template>

<style scoped lang="scss">
.edit {
    position: relative;

    height: 48px;

    padding: 8px 16px;

    border: 1px solid $border-subtle;
    border-radius: $border-radius-m;

    &.focused {
        border: 1px solid $accent-moderate;
        box-shadow: $shadow-medium;
    }

    &.filled &__placeholder,
    &__input:focus + &__placeholder {
        top: 8px;
        transform: translateY(0);

        font-size: $font-size-s;
    }

    &__input {
        font-size: $font-size-l;

        width: 100%;
        height: 100%;

        padding-top: 8px;

        border: none;
        outline: none;
        background-color: transparent;

        position: relative;
        z-index: 2;
    }

    &__placeholder {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        transition:
            top 0.4s ease,
            transform 0.4s ease,
            font-size 0.4s ease;
    }
}
</style>
