<template>
  <div>
      <div>
        <h3>Main 화면입니다.</h3>
        <div v-if="$fetchState.pending">
          로딩 중입니다.
        </div>
        <div v-else>
          로딩 끝
        </div>
        <div>
        {{$fetchState}}
          <h3>{{rendering}}</h3>
        </div>
        <div v-if="list.length > 0">
          <ul>
            <li v-for="(item, index) in list" :key="index">
              <span v-text="item.name"></span>
              <span v-text="item.value"></span>
            </li>
          </ul>
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
