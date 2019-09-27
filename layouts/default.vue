<template>
  <div class="container-wrap">
    <header>
      <p>Laravel Admin<span>Manage your laravel</span></p>
    </header>
    <nuxt />
  </div>
</template>

<style lang="scss">
  header{
      --height:4.5rem;
      width:100%;
      height: var(--height);
      color: #fff;
      font-size: 1.2rem;
      line-height: var(--height);
      padding-left: 2.3rem;
      background-image: linear-gradient(to right bottom, #276ace, #29bdd9);
      margin-bottom: 2.4rem;
      box-sizing: border-box;
    span{
      margin-left: 1rem;
      font-size: .7rem;
    }
  }
  .container-wrap{
    height: 100%;
    display: flex;
    flex-direction: column;
  }
</style>
