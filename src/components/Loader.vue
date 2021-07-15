<template>
    <div class="loader">
       Loading...
    </div>    
</template>


<script>
export default {
    name: "Loader"
}
</script>


<style lang="scss" scoped>

    .loader {
        position: fixed;
        left: 0;
        width: 100%;
        height: 100vh;
        background: #fff;
        display: flex;
        justify-content: center;
        align-items: center;
    }

</style>