<template>
  <div class="container">
    <h1>Posts</h1>
    <p class="text-muted" />

    <hr class="mb-4" />

    <div class="row">
      <div
        v-for="(item, index) in sortedPosts"
        :key="index"
        class="col-md-6 px-lg-5"
      >
        <div
          class="border-left-0 border-right-0 border-top-0 card hvr-shadow mb-4 w-100"
        >
          <router-link :to="'posts/' + urlize(item.title)">
            <div class="img-wrapper" data-aos="flip-down">
              <img
                v-lazy="require('../assets/img/posts/' + item.img)"
                :alt="item.title"
                class="card-img-top hvr-grow"
              />
            </div>

            <div
              class="card-body d-flex flex-column text-left"
              data-aos="flip-up"
            >
              <small>{{ item.date }} / {{ item.tag }}</small>
              <h3 class="card-title h5 text-dark">{{ item.title }}</h3>
              <p class="card-text small text-muted">{{ item.description }}</p>

              <router-link
                to="'posts/' + urlize(item.title)"
                class="d-flex align-items-center ml-auto small"
                >Read more —</router-link
              >
            </div>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { urlize } from "@/assets/js/functions";
import { posts } from "@/assets/js/data";

export default {
  data() {
    return {
      posts
    };
  },
  computed: {
    sortedPosts() {
      return posts.reverse();
    }
  },
  methods: {
    urlize
  }
};
</script>
