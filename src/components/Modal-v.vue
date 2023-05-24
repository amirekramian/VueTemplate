<template>

    <div class="backdrop">
        <div class="modal">
            <img class="height" src="~\src\assets\Outlander.jpg" alt="">
            <p>modal content</p>
        </div>
    </div>
</template>

<script>

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