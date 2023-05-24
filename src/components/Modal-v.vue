<template>
    <div class="backdrop">
        <div class="modal">
            <h2>{{ BookData }}</h2>
            <p>modal content</p>
        </div>
    </div>
</template>

<script>
export default {
    props:['BookData']
}
</script>


<style scoped>
.modal{
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
}

.backdrop{
    top:0;
    position: fixed;
    background: rgba(0, 0, 0, 0.3);
    width: 100%;
    height: 100%;
}
img.height{
 max-height: 200px;
}
</style>