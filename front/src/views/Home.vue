<template>
  <div class='container'>
    <GarbageDay/>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import MyButton from '@/components/MyButton.vue'; // @ is an alias to /src
  import GarbageDay from '@/components/GarbageDayTable.vue';

  export default defineComponent({
    name: 'Home',
    components: {
      MyButton,
      GarbageDay
    },
  });
  </script>
