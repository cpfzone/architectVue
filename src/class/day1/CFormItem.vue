<template>
    <div>
        <label v-if="title" >{{ title }}</label>
        <slot />
        <p v-if="errMsg">{{errMsg}}</p>    
    </div>
</template>

<script>
import Schema from "async-validator";

    export default {
        inject: ['form'],
        data() {
            return {
                errMsg: ''
            }
        },
        props: {
            title: {
                type: String,
                default: ''
            },
            prop: {
                type: String
            } 
        },
        mounted () {
            this.$on('validate', this.validate)
        },
        methods: {
            validate() {
                // 1.拿到value
                const value = this.form.model[this.prop]
                // 2.拿到rule, 拿到提示信息
                const rule = this.form.rules[this.prop]
                const desc = {[this.prop]: rule}
                const schema = new Schema(desc)
                return schema.validate({[this.prop]: value}, err => {
                    if (err) {
                        this.errMsg = err[0].message
                    }else{
                        this.errMsg = ''
                    }
                })

            }
        },
    }
</script>

<style>

</style>