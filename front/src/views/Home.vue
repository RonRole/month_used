<template>
  <div class="home">
    <MyButton text='Hello'></MyButton>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import MyButton from '@/components/MyButton.vue'; // @ is an alias to /src

  export default defineComponent({
    name: 'Home',
    components: {
      MyButton,
    },
  });
  </script>
