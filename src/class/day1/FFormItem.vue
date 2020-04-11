<template>
    <div>
        <label v-if="title">{{title}}</label>
        <slot />
    </div>
</template>

<script>
    export default {
        name: 'FFormItem',
        props: {
            title:String,
            props:String
        }
    }
</script>

<style scoped>

</style>