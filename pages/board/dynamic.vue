<template>
   <div>
      <div>
         <h3>동적 생성 link 만들기</h3>
         <p>vue 페이지 이름을 동적으로 링크하기</p>
      </div>
      <div>
         <ul v-for="item in mountains" :key="item.id">
            <NuxtLink :to="`/board/${item.continent.toLowerCase()}/${item.slug}`">
               <li>{{ item.title }}</li>
            </NuxtLink>
         </ul>
      </div>
   </div>
</template>
<script>
export default {
   async asyncData() {
      const mountains = await fetch(
         'https://api.nuxtjs.dev/mountains'
      ).then( res => res.json());

      return { mountains }
   }
}
</script>