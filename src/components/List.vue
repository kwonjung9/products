<template>
  <div class="product-list">
    <div class="card" v-for="list in products" :key="list.id">
      <img :src="list.image" :alt="list.name">
      <p>{{ list.name }}</p>
      <p>{{ list.price }}￦</p>
      <button @click="addToList(list)">장바구니 추가</button>
    </div>
  </div>
</template>

<script setup>
  defineProps({
    products:Array
  });
  const emit = defineEmits(['add-to-cart']);
  const addToList = (list)=>{
    emit( 'add-to-cart', list );
  }
</script>

<style lang="scss" scoped>
  .product-list{
    display: flex;
    gap: 2rem;
    justify-content: center;
    .card{
      padding: 60px 0;
      width: 200px;
      text-align: center;
      p:nth-of-type(1){
        font-size: 1.2rem;
      }
      img{
        width: 100%;
        height: 200px;
        object-fit: contain;
        border-radius: 5px;
        padding: 10px;
      }
      button{
        margin: 10px 0;
        padding: 10px;
        border-radius: 10px;
        border: none;
      }
      button:hover{
        background-color: #444;
      }
    }
  }
</style>