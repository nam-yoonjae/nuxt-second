<template>
  <div>
      <NavigationMain></NavigationMain>
      <div>
        <h3>Board 메인 화면입니다.</h3>
        <Nuxt-link to="/board/board_list">게시판으로</Nuxt-link>
      </div>
  </div>
</template>

<script>
export default {
  layout : 'board',
}
</script>

<style>
</style>
