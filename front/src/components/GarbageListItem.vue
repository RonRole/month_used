<template>
    <li v-bind:class="['list-group-item',{'active':data.isActive}]">
        <slot />
    </li>
</template>

<script lang="ts">
    import { defineComponent } from "vue";

    class ActiveDay {
        private date : Date;
        private activeDay : Number;
        private activeTimesOfDay : Array<Number> 

        constructor(date: Date, activeDay : Number, activeTimesOfDay : Array<Number>) {
            this.date = date;
            this.activeDay = activeDay;
            this.activeTimesOfDay = activeTimesOfDay;
        }

        public isActive(): Boolean {
            const isActiveDay = this.isDayOf(this.activeDay)
            const isActiveTimesOfMonth = this.activeTimesOfDay.some(element => {
                return element === this.dayCountOfMonth()
            })
            return isActiveDay && isActiveTimesOfMonth
        }

        private isDayOf(day : Number) : Boolean {
            return day === this.date.getDay()
        }

        private dayCountOfMonth(): Number {
            const devide = this.date.getDate() / 7
            if(devide <= 1) {
                return 1
            }
            if(1 < devide && devide <= 2) {
                return 2
            }
            if(2 < devide && devide <= 3) {
                return 3
            }
            if(3 < devide && devide <= 4) {
                return 4
            }
            if(4 < devide) {
                return 5
            }
            return 0;
        }
    }

    interface Props {
        targetDate: Date,
        activeDayNum: Number,
        activeTimesOfDay: Array<Number>
    }

    export default defineComponent({
        name: 'GarbageListItem',
        props: {
            targetDate: {
                default: () => new Date(),
                required: true
            },
            activeDayNum: {
                type: Number,
                required: true,
                validator: val => [0,1,2,3,4,5,6].some(e => e === val)
            },
            activeTimesOfDay: {
                default: () => [1,2,3,4,5]
            }
        },
        setup(props: Props) {
            const today = new ActiveDay(props.targetDate, props.activeDayNum, props.activeTimesOfDay)
            const data = {
                isActive: today.isActive()
            }
            return {
                data
            }
        }
    })
</script>

<style scoped>
    p {
        padding: 0;
        margin: 0;
    }
</style>