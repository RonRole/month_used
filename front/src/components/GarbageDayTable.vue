<template>
    <table class="table">
        <thead>
            <tr>
                <th class="bg-dark text-light" scope="col">曜日</th>
                <th class="bg-dark text-light" scope="col">分類</th>
                <th class="bg-dark text-light" scope="col">手法</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <th scope="row">月</th>
                <td>
                    <GarbageListItem :targetDate=targetDate :activeDayNum=1>
                        <p>【回収なし】</p>
                    </GarbageListItem>
                </td>
                <td>
                    blank
                </td>
            </tr>
            <tr>
                <th scope="row">火</th>
                <td>
                    <ul class="list-group">
                        <GarbageListItem :targetDate=targetDate :activeDayNum=2>
                            <p>一般ごみ</p>
                            <p>有害ごみ</p>
                        </GarbageListItem>
                    </ul>
                </td>
                <td>blank</td>
            </tr>
            <tr>
                <th scope="row">水</th>
                <td>
                    <ul class="list-group">
                        <GarbageListItem :targetDate=targetDate :activeDayNum=3 :activeTimesOfDay=[1,3]>  
                            <strong>第1, 第3</strong>
                            <p>プラスチック製包装容器</p>
                            <p>ペットボトル</p>
                            <p>繊維類</p>
                        </GarbageListItem>
                        <GarbageListItem :targetDate=targetDate :activeDayNum=3 :activeTimesOfDay=[2,4]>
                            <strong>第2, 第4</strong>
                            <p>プラスチック製包装容器</p>
                            <p>びん</p>
                            <p>飲料かん</p>
                        </GarbageListItem>
                        <GarbageListItem :targetDate=targetDate :activeDayNum=3 :activeTimesOfDay=[5]>
                            <strong>第5</strong>
                            <p>【回収なし】</p>
                        </GarbageListItem>
                    </ul>
                </td>
                <td>blank</td>
            </tr>
            <tr>
                <th scope="row">木</th>
                <td>
                    <ul class="list-group">
                        <GarbageListItem :targetDate=targetDate  :activeDayNum=4 :activeTimesOfDay=[1,3]>  
                            <strong>第1, 第3</strong>
                            <p>一般ごみ</p>
                            <p>有害ごみ</p>
                            <p>金属類</p>
                            <p>紙類</p>
                        </GarbageListItem>
                        <GarbageListItem :targetDate=targetDate  :activeDayNum=4 :activeTimesOfDay=[2,4]>
                            <strong>第2, 第4</strong>
                            <p>一般ごみ</p>
                            <p>有害ごみ</p>
                        </GarbageListItem>
                        <GarbageListItem :targetDate=targetDate  :activeDayNum=4 :activeTimesOfDay=[5]>
                            <strong>第5</strong>
                            <p>【回収なし】</p>
                        </GarbageListItem>
                    </ul>
                </td>
                <td>blank</td>
            </tr>
            <tr>
                <th scope="row">金</th>
                <td>
                    <GarbageListItem :targetDate=targetDate  :activeDayNum=5>
                        <p>【回収なし】</p>
                    </GarbageListItem>
                </td>
                <td>blank</td>
            </tr>
        </tbody>
    </table>
</template>

<script lang="ts">
import {computed, defineComponent, Prop, PropType} from 'vue'
import GarbageListItem from '@/components/GarbageListItem.vue'

interface Props {
    targetDate: Date
}
export default defineComponent({
    name: 'GarbageDayTable',
    components: {
        GarbageListItem
    },
    props: {
        targetDate: {
            type: Object as PropType<Date>,
            required: true
        }
    },
    setup(props: Props) {
        const targetDate = computed(()=>props.targetDate)
        return {
            targetDate
        }
    }
})
</script>

<style scoped>
    p {
        padding:0;
        margin: 0;
    }

    thead th {
        position: -webkit-sticky;
        position: sticky;
        top: 0;
        z-index: 9999;
    }
</style>