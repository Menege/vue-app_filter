<template>
  <div>
    <div class="container">
      <div class="input-block">
        <div class="input-block__border">
          <div class="input-block__border_img">
            <img
              width="15"
              height="15"
              src="./assets/search-icon.png"
              alt="Search..."
            />
          </div>
          <input placeholder="Filter by..." class="input" v-model="search" />
        </div>
      </div>
      <div class="wrapped" v-if="filteredPosts">
        <div class="row">
          <div
            class="col-md-4 block-items_item"
            v-for="(item, idx) in filteredPosts"
            :key="item.id"
          >
            <Cart
              :name="item.name"
              :title="arrayPosts[idx].title"
              :disc="arrayPosts[idx].body"
            />
          </div>
        </div>
      </div>
      <div class="search-empty" v-else>
        No results were found for your search term...
      </div>
    </div>
  </div>
</template>

<script>
import Cart from "./components/Cart.vue";

export default {
  data() {
    return {
      arrayPosts: null,
      users: null,
      search: "",
      disc: "",
      name: "",
    };
  },
  name: "App",
  created() {
    fetch("http://jsonplaceholder.typicode.com/posts")
      .then((response) => response.json())
      .then((data) => (this.arrayPosts = data));
    fetch("http://jsonplaceholder.typicode.com/users")
      .then((response) => response.json())
      .then((data) => (this.users = data));
  },
  components: {
    Cart,
  },
  computed: {
    filteredPosts() {
      let search = this.search;
      let filteredArray;

      if (this.users) {
        filteredArray = this.users.filter(function (elem) {
          if (search === "") return true;
          else return elem.name.indexOf(search) > -1;
        });
        if (!filteredArray.length) return false;
        return filteredArray;
      }
      return false;
    },
  },
};
</script>

<style>

</style>
