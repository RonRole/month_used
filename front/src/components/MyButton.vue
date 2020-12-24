<template>
    <button @click='sawai'>{{data.text}}</button>
</template>

<script lang="ts">
    import {defineComponent, reactive} from 'vue'
    
    interface Props {
        text: String
    }

    interface Data {
        text: String
    }
    
    export default defineComponent({
        props : {
            text: {
                type: String,
                default: 'ぷももボタン'
            }
        },
        setup(props: Props) {
            const data = reactive({
                text: props.text
            })
            const sawai = () : void => {
                alert(data.text)
            }
            return {
                data,
                sawai,
            }
        }
    })
</script>