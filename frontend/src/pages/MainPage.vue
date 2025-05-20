<template>
  <div class="container">
    <br />
    <div id="welcome" class="text-center">
      <img src="@/assets/welcome2.png" width="50%" />
    </div>

    <b-row>
      <b-col></b-col>
      <b-col></b-col>

      <b-col cols="5" class="RandomRecipesCol">
        <div v-if="isLoading" class="loader-container">
          <b-spinner variant="warning" label="Loading..." class="my-3" />
          <p>This may take a few seconds...</p>
        </div>

        <RecipePreviewList
          v-else
          route_name="/recipes/random"
          title="Explore this recipes"
          class="RandomRecipes center"
          @loaded="isLoading = false"
        />

        <b-button tag="button" pill @click="new_random_recipes" class="buttonwelc">
          Click for new 3 recipes!
        </b-button>
      </b-col>

      <b-col></b-col>

      <b-col cols="4">
        <RecipePreviewList
          v-if="$root.store.username"
          route_name="/users/getThreeLast"
          title="Last watched recipes"
          class="LastViewedRecipes center"
        />
        <LogIn
          v-else
          width="200px"
          title="Log In"
          class="Log In center"
        />
      </b-col>

      <b-col></b-col>
      <b-col></b-col>
      <b-col></b-col>
    </b-row>
  </div>
</template>

<script>
import RecipePreviewList from "../components/RecipePreviewList";
import LogIn from "../components/LogIn.vue";

export default {
  components: {
    RecipePreviewList,
    LogIn
  },
  data() {
    return {
      isLoading: true
    };
  },
  methods: {
    new_random_recipes() {
      this.isLoading = true;
      setTimeout(() => {
        window.location.reload();
      }, 200);
    }
  }
};
</script>

<style lang="scss" scoped>
.container {
  border-radius: 27px;
  max-width: 1900px;
}

.center {
  margin-left: auto;
  margin-right: auto;
}

.title {
  color: #cfa343;
  font-weight: bolder;
}

.big-title {
  font-family: Georgia, 'Times New Roman', Times, serif;
  font-size: 48px;
  color: #cfa343;
}

.buttonwelc {
  width: 40%;
  font-family: Georgia, serif;
  font-size: 23px;
  padding: 14px 14px;
  background-color: #cfa343;
  border-color: #cfa343;
  font-weight: bold;
  color: #080807;
  margin-left: 235px;
  border-radius: 50%;
}

.buttonwelc:hover {
  background-color: #cfa343b5;
  color: white;
}

.log {
  font-family: Georgia, 'Times New Roman', Times, serif;
  font-size: 48px;
  color: #cfa343;
  font-weight: bolder;
}

.loader-container {
  text-align: center;
  margin-top: 30px;
  font-size: 18px;
  color: #cfa343;
}
</style>
