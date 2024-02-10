<script setup>
const props = defineProps({
    title: String
})
</script>

<template>
    <header class="header">
        <h1 class="header__title">{{ title }}</h1>
    </header>
</template>

<style scoped lang="scss">
.header {
    background-color: $accent-intense;
    color: $accent-subtle;
    text-align: center;
    padding-block: 10px;
    border-radius: $border-radius-l $border-radius-l 0 0;
}
</style>
