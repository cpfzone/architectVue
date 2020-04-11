<template>
    <div>
        <slot/>
    </div>
</template>

<script>
    export default {
        name: 'FForm',
        provide() {
            return {
                form: this
            }
        },
        props: {
            model: {
                type: Object,
                required: true
            },
            rules: {
                type: Object
            }
        }
    }
</script>

<style scoped>

</style>