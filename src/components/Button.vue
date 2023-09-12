<template>
    <button class="btn" :style="{backgroundColor: color}" @click="openForm()">
        {{ title }}
    </button>
</template>

<script>
    export default {
        name: 'Button',
        props:{
            title: String,
            color: String
        },
        methods:{
            openForm(){
                this.$emit("toggle-add-task")
            }
        }
    }
</script>

<style scoped>
</style>
