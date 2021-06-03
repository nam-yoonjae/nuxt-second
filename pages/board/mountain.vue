<template>
  <div>
      <div>
        <h3>Nuxt Mountains 예제</h3>
        <Nuxt-link to="/board/">게시판 첫 화면으로</Nuxt-link>
        <div>
          <p v-if="$fetchState.pending">Fetching mountains...</p>
          <p v-else-if="$fetchState.error">An error occured :(</p>
          <div v-else>
            <ul>
              <li class="mountain-list" v-for="(item, index) in list" :key="index">
                <h3>이름 : {{item.title}}</h3>
                <img :src="item.image" width="30%;">
                <p>대륙 : {{item.continent}}</p>
                <p>설명 : {{item.description}}</p>
                <p>국가 : <span v-for="(country, index2) in item.countries" :key="index2"> {{country}} </span></p>
                <p>높이 : {{item.height}}</p>
              </li>
            </ul>
            <button @click="$fetch">Refresh</button>
          </div>
        </div>
      </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        list : [],
      }
    },
    async fetch() {

      this.getData();

    },
    methods : {

      getData() {
        const url = 'https://api.nuxtjs.dev/mountains';
        let _self = this;
        this.$axios.post( url ).then( res => {
          if( 200 == res.status ) {
            console.log( res.data );
            _self.list = res.data;
          }
        })
      }
    },
  }
</script>

<style>
.mountain-list {
  padding-top:1rem;
}
</style>
