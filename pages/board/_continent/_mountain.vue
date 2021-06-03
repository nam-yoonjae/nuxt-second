<template>
   <div>
      <h1>대륙 : {{ continent }}</h1>
      <h2>산 이름 : {{ mountain }}</h2>
      <p>Path : {{ $route.path }}</p>
      <NuxtLink to="/board/">to Back  </NuxtLink>
   </div>
</template>
<script>
export default {
   async asyncData({ params, redirect }) {
      
      const mountains = await fetch(
         'https://api.nuxtjs.dev/mountains'
      ).then( res => res.json() );

      const filteredMountain = mountains.find(
         ( mountain ) =>  
         mountain.continent.toLowerCase() === params.continent &&
         mountain.slug === params.mountain
      );

      if ( filteredMountain ) {
         return {
            continent : filteredMountain.continent,
            mountain : filteredMountain.title
         }
      }
      else {
         redirect('/');
      }

   }
}
</script>