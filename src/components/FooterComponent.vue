<template>
    <footer class="text-center m-0 p-0">
        <h5>Made with <i class="fa-solid fa-heart"></i></h5>
    </footer>
</template>

<script>
export default {
  name: 'FooterComponent',
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
footer{
    height: 5vh;
    background-color: rgba(69, 69, 69, 0.171);
    h5{
        line-height: 5vh;
    }
}
</style>