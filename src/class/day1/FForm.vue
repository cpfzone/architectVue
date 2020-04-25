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
        },
        methods: {
            validate(cb) {
               const tasks = this.$children.filter(item => item.prop).map(item=> item.validate())
               Promise.all(tasks).then(res=>{
                   cb(true)
               }).catch(err=>{
                   cb(false)
               })
            }
        }
    }
</script>

<style scoped>

</style>