<script setup>
import { reactive } from 'vue'

import Edit from '@/components/Edit.vue'
import BasicButton from '@/components/BasicButton.vue'

const eventData = reactive({
    name: null,
    description: null,
    date: null,
    timeOn: null,
    timeOff: null
})
</script>

<template>
    <div class="event">
        <h2 class="event__title">Event</h2>

        <div class="event__edit-group">
            <Edit v-model="eventData.name" placeholder="Name" />
        </div>

        <div class="event__edit-group">
            <Edit v-model="eventData.description" placeholder="Description" />
        </div>

        <div class="event__edit-group">
            <Edit v-model="eventData.date" placeholder="Date" />
        </div>

        <div class="event__edit-group">
            <Edit v-model="eventData.timeOn" placeholder="Time on" />
        </div>

        <div class="event__edit-group">
            <Edit v-model="eventData.timeOff" placeholder="Time off" />
        </div>

        <div class="event__buttons">
            <BasicButton>Save</BasicButton>
        </div>
    </div>
</template>

<style scoped lang="scss">
.event {
    &__title {
        margin: 0 0 16px 8px;
    }

    &__edit-group {
        margin-bottom: 16px;

        &:last-of-type {
            margin-bottom: 64px;
        }
    }

    &__buttons {
        display: flex;
        justify-content: center;
    }
}
</style>
