<script>
import CirclesComponent from "@/components/CirclesComponent.vue";
import PostComponent from "@/components/PostComponent.vue";
import AccountComponent from "@/components/AccountComponent.vue";
import data from "@/data.json";
import { useLikeStore } from "@/stores/likes.js";

export default {
  name: "HomeView",
  components: {
    AccountComponent,
    CirclesComponent,
    PostComponent
  },
  data() {
    return {
      posts: data.posts,
      accounts: data.accounts,
      likeStore: useLikeStore()
    }
  }
}
</script>

<template>
  <section class="home">

    <article class="middle">
      <section class="top-part-section">
        <RouterLink to="/" class="top-part">For you</RouterLink>
        <RouterLink to="/" class="top-part">Followed</RouterLink>
      </section>

      <section class="circles">
        <CirclesComponent v-for="account in accounts.slice(0, 4)" :key="account.id" :account="account" :off=0 />
      </section>
      <PostComponent v-for="post in likeStore.likes" :key="post" :post="posts[post-1]" class="post"/>
    </article>
    <section class="right-side">
      <h2>Suggestions for you</h2>
      <AccountComponent v-for="account in accounts.slice(4, 8)" :key="account.id" :account="account" :off=1 />
      <p>Information • Help • Press releases• API • Work opportunities • Privacy • Terms
        • Localities • Language • Meta Verified</p>
      <p class="bottom-text">© 2025 Instagram from Marek</p>
    </section>

  </section>
</template>

<style scoped>
  .top-part-section {
    display: flex;
    gap: 20px;
    border-bottom: rgba(255, 255, 255, .15) solid 2px;
    padding: 10px 0;
    min-width: 100%;
  }
  .top-part {
    text-decoration: none;
    color: white;
    font-weight: bold;
    font-size: 1.2rem;
  }
  .circles {
    display: flex;
    gap: 20px;
    text-decoration: none;
    flex-wrap: wrap;
    max-width: 420px;
  }
  .middle {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .post {
    max-width: 100%;
  }
  .right-side {
    margin: 4rem 0 0 5rem;
    max-width: 300px;
  }
  @media only screen and (max-width: 1090px) {
    .right-side {
      margin-left: 1rem;
    }
  }
  @media only screen and (max-width: 1010px) {
    .right-side {
      display: none;
    }
  }
  .home {
    display: flex;
    justify-content: center;
  }
  h2 {
    font-family: "Segoe UI", sans-serif;
    font-size: 1.2rem;
    color: rgba(255, 255, 255, .55);
    font-weight: normal;
  }
  p {
    margin-top: 3rem;
    color: rgba(255, 255, 255, .55);
  }

</style>