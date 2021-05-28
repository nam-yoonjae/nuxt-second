<template>
   <div>
      <h1 v-if="error.statusCode === 404">
         Page Not Found
      </h1>
      <h1 v-else>An Error Occurred</h1>
      <NuxtLink to="/">To Home Page</NuxtLink>
   </div>
</template>
<script>
export default {
   props : ['error'],
   layout : 'error'
}
</script>