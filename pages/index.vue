<template>
  <div>
      <div>
        <h3>Main 화면입니다.</h3>
        <div>
        {{$fetchState}}
          <h3>{{rendering}}</h3>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title : this.title,
      meta : [
        {
          name : 'description',
          content : 'my custom content',
        }
      ],
    }
  },
  data() {
    return {
      list : [],

      title : `Cheeeez's Website`,
    }
  },
  computed : {

  },
  async fetch() {
    this.makeList();
  },

  asyncData() {
    return {
      rendering : process.server ? 'server' : 'client'
    }
  },

  methods : {
    
    // 목록을 만듭니다.
    makeList() {
      let tempArr = [];
      let index = 0;
      for( index; index < 10; index++){
        let tempObj = {
          name : 'test',
          value : index,
        };
        tempArr.push(tempObj);
      }
      this.list = tempArr;
    },
  },


}
</script>

<style>
</style>
