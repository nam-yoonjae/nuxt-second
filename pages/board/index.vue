<template>
  <div>
      <div>
        <h3>Board 메인 화면입니다.</h3>
          <ul>
            <li>
              <Nuxt-link to="/board/mountain">Nuxt.js Mountains 목록</Nuxt-link>
            </li>
            <li>
              <Nuxt-link to="/board/dynamic">Nuxt.js dynamicPages</Nuxt-link>
            </li>
            <li>
              <NuxtLink to="/board/datafetching">asyncData Example</NuxtLink>
            </li>
          </ul>
      </div>
  </div>
</template>

<script>
export default {
}
</script>

<style>
</style>
