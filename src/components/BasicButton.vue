<script setup></script>

<template>
    <button class="basic-button">
        <slot></slot>
    </button>
</template>

<style scoped lang="scss">
.basic-button {
    padding: 16px 150px;
    max-width: 360px;

    background-color: $accent-moderate;
    color: $accent-subtle;

    font-weight: 700;
    font-size: $font-size-l;

    border-radius: $border-radius-x;
    border: none;

    cursor: pointer;

    transition:
        background-color 0.2s ease,
        scale 0.2s ease;

    &:hover {
        background-color: $accent-bold;
    }

    &:active {
        background-color: $accent-strong;
    }

    &:hover,
    &:active {
        scale: 1.05;
    }
}
</style>
