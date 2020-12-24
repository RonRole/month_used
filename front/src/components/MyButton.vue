<template>
    <button @click='sawai("ぷももえんぐえげぎぎおんもえちょっちょっちゃっさ！")'>{{greet}}</button>
</template>

<script lang="ts">
    import {defineComponent} from 'vue'
    export default defineComponent({
        props: {
            greet: String,
        },
        methods: {
            sawai: (input:string) : void => {
                alert(input)
            }
        }
    })
</script>