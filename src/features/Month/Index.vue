<script setup>
import { ref } from 'vue'
import Container from '@/components/Container.vue'
import Header from '@/components/Header.vue'
import Day from '@/features/Month/MonthDay.vue'
import Popup from '@/components/Popup.vue'
import Event from '@/features/Month/Event.vue'

const days = ref([])
const weekDays = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']

const currentMonth = new Date().toLocaleString('default', { month: 'long' })
const daysCount = new Date(new Date().getFullYear(), new Date().getMonth() + 1, 0).getDate()

const firstMonthWeekDay = new Date(new Date().getFullYear(), new Date().getMonth(), 1).getDay()
const weekDaysCount = 7

const emptyStartDays = Array.from({ length: firstMonthWeekDay - 1 }, (_, i) => i + 1)
const emptyEndDays = Array.from(
    { length: weekDaysCount - ((emptyStartDays.length + daysCount) % weekDaysCount) },
    (_, i) => i + 1
)

days.value = [
    ...emptyStartDays.map(() => ''),
    ...Array.from({ length: daysCount }, (_, i) => i + 1),
    ...emptyEndDays.map(() => '')
]
</script>

<template>
    <div class="month">
        <Container>
            <Header :title="currentMonth" />

            <div class="month__body">
                <div class="month__week-days">
                    <div
                        class="month__week-day"
                        v-for="day in weekDays"
                        :key="`month-week-day-${day}`"
                    >
                        {{ day }}
                    </div>
                </div>

                <div class="month__days">
                    <Day v-for="(value, index) in days" :key="`month-day-${index}`" :day="value" />
                </div>
            </div>
        </Container>

        <Popup :show="true">
            <Event />
        </Popup>
    </div>
</template>

<style scoped lang="scss">
.month {
    &__body {
        border: 1px solid $border-subtle;
        box-shadow: $shadow-high;
    }

    &__week-days {
        display: grid;
        grid-template-columns: repeat(7, 1fr);
        grid-auto-rows: 50px;

        font-size: $font-size-l;

        border-bottom: 1px solid $border-subtle;

        background-color: $accent-subtle;
    }

    &__week-day {
        width: calc(100% - 1px);
        height: 100%;

        display: flex;
        justify-content: center;
        align-items: center;

        &:not(:last-child) {
            border-right: 1px solid $border-subtle;
        }
    }

    &__days {
        display: grid;
        grid-template-columns: repeat(7, 1fr);

        aspect-ratio: 1.4 / 1;
    }
}
</style>
