<template>
  <div>
    <b-button :variant="variant">
        <slot>
            {{text}}
        </slot>
    </b-button>
  </div>
</template>

<script>
export default {
    props:{
        text:{
            type:String,
            default: 'Padrão' 
        },
        variant:{
            type:String,
            default:'primary'
        }
    }
};
</script>

<style lang="scss" scoped></style>
