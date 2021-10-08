<template>
    <div>
        <b-form-input :type="types"></b-form-input>
    </div>
</template>

<script>
export default {
    props:{
        types:{
            type:String,
            default:'text'
        }
    }
}
</script>

<style lang="scss" scoped>

</style>