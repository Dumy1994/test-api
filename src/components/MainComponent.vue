<template>
  <main class="row p-0 m-0">
    <!-- input cerca card  -->
    <div class=" d-flex flex-column justify-content-center align-items-center container-cerca">
      <h1 class="title">Cerca un post</h1>
      <input
        type="text"
        placeholder="Search"
        v-model="search"
        @keyup.enter="cerca"
        minlength="3"
      />
      <div v-if="show"><h6>Inserisci una parola maggiore di 3 caratteri</h6></div>
      <button @click="cerca">Cerca</button>
    </div>
    <!-- print cards  -->
    <div v-for="(item, index) in items.slice(0, 20)" :key="index" class="col-sm-12 col-md-6 col-lg-6 ">
      <div class="text-center card">
        <h2 class="m-3">
          <i class="fa-solid fa-user"></i>
          {{ items[index].name }}
        </h2>
        <h5>
          <i class="fa-solid fa-envelope"></i>
          {{ items[index].email }}
        </h5>
        <p>
          <i class="fa-solid fa-file-lines"></i>
          {{ items[index].body.substring(0, 64) + '...' }}
        </p>
      </div>
    </div>
    <!-- if items empity  -->
    <div  v-if="items.length == 0 && nessunPost" class="col-sm-12 col-md-12 col-lg-12 ">
      <div class="text-center card">
        <h2 class="m-3">
          <i class="fa-solid fa-user"></i>
          Nessun post trovato 
        </h2>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "MainComponent",
  props: {
    items: Array,
  },
  data() {
    return {
      search: "",
      show: false,
      nessunPost: false,
    };
  },
  methods: {
    cerca() {
      if (this.search.length > 3) {
        this.$emit("performSearch", this.search);
        this.nessunPost= true;
        this.show = false;
        
      }else{
        this.show = true;
      }
    },
  },
};
</script>

<style lang="scss">
@import "../style/general.scss";
main {
  height: 90vh;
  overflow: scroll;
  // container cerca 
  .container-cerca{
    input{
    width: 30%;
    border-radius: 5px;
    border: 2px solid rgb(29, 189, 136);
    
    }
    .title{
      margin-bottom: 20px;
      color: rgb(29, 189, 136);
      font-size: 3.5rem;
    }
    h6{
      color: rgb(186, 3, 3);
    }
    button{
      margin-top: 10px;
      background-color: rgb(29, 189, 136);
      padding: 5px;
      width: 100px;
      border: 0;
      border-radius: 5px;
      &:hover{
        transform: scale(1.1);
        color: white;
      }
    }
  }
  // container cards 
  .card{
    height: 28vh;
    margin: 10px;
    h2{
      color:  rgb(29, 189, 136);
    }
    h5{
      color: rgb(118, 115, 115);
    }
  }
  // input 
  ::placeholder {
    color: rgb(29, 189, 136);
  } 
  input[type=text]:focus{
  outline: 1px solid #28a745;  
  box-shadow: 0 0 15px #719ECE;   
}
}
</style>