<template>
    <div class="test">
        This is header
        <slot name="HeaderMore">
        <slot>Default Content</slot>
        </slot>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="css" scoped>
    
    .test{
        background-color:blanchedalmond ;
        width: 100%;
        height: 300px;
    }
</style>