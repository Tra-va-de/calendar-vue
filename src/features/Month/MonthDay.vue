<script setup>
const props = defineProps({
    day: {
        type: [Number, String],
        required: true
    }
})
</script>

<template>
    <div class="day">
        <div class="day__number">{{ props.day }}</div>
    </div>
</template>

<style scoped lang="scss">
.day {
    padding: 10px;

    &:not(:nth-of-type(7n)) {
        border-right: 1px solid $border-subtle;
    }

    &:not(:nth-last-child(-n + 7)) {
        border-bottom: 1px solid $border-subtle;
    }

    &__number {
        font-size: $font-size-xs;
        font-weight: 400;
    }
}
</style>
