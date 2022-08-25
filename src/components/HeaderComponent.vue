<template>
    <header class=" p-0">
        <h1>Posts</h1>
    </header>
</template>

<script>
export default {
  name: 'HeaderComponent',
    data() {
        return {
        }
        
    },
    mounted() {
    },
  
}
</script>

<style lang="scss">
@import "../style/general.scss";

header{
    background-color: rgb(29, 189, 136);
    height: 5vh;
    h1{
        line-height: 5vh;
        color: white;
        margin-left: 22px;
    }
}
</style>