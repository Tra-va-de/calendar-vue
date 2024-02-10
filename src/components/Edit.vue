<script setup>
const props = defineProps({
    placeholder: String
})
</script>

<template>
    <div class="edit">
        <input class="edit__input" type="text" />

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
        border: 1px solid $accent-bold;
        box-shadow: 0 0 0 1px $accent-moderate;
    }

    &.focused &__placeholder,
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
