<template>
  <div class='container'>
    <select class="form-control" @change="changeDate">
        <option>{{today.toStringBefore()}}</option>
        <option selected>{{today.toString()}}</option>
        <option>{{today.toStringAfter()}}</option>
    </select>
    <GarbageDayTable :targetDate=targetDate />
  </div>
</template>

<script lang="ts">
  import { defineComponent, reactive, ref } from 'vue';
  import MyButton from '@/components/MyButton.vue'; // @ is an alias to /src
  import GarbageDayTable from '@/components/GarbageDayTable.vue';

  class Today {

    private date : Date;

    constructor(date: Date) {
      this.date = date
    }

    toStringBefore() {
      return `${this.date.getUTCFullYear()}/${this.date.getMonth()+1}/${this.date.getDate()-1}`
    }
    
    toString() {
      return `${this.date.getUTCFullYear()}/${this.date.getMonth()+1}/${this.date.getDate()}`
    }

    toStringAfter() {
      return `${this.date.getUTCFullYear()}/${this.date.getMonth()+1}/${this.date.getDate()+1}`
    }    
  }
  export default defineComponent({
    name: 'Home',
    components: {
      MyButton,
      GarbageDayTable
    },
    setup() {
      const today = new Today(new Date())
      const targetDate = ref<Date>(new Date())
      const changeDate = (e: Event) => {
        if(e.target instanceof HTMLSelectElement) {
          const input = e.target.value.split('/').map(value => Number.parseInt(value)) 
          targetDate.value = new Date(input[0], input[1]-1, input[2])
        }
      }
      return {
        today,
        targetDate,
        changeDate
      }
    }
  });
</script>