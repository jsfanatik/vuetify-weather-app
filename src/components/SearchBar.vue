<template>
    <!-- <v-app id="inspire"> -->
      <v-app-bar flat>
        <v-container class="fill-height d-flex align-center py-2">
          <v-avatar
            class="me-10 ms-4"
            color="grey-darken-1"
            size="32"
          ></v-avatar>

          <!-- <v-btn
            v-for="link in links"
            :key="link"
            variant="text"
          >
            {{ link }}
          </v-btn> -->

          <!-- <v-text-field label="Label"></v-text-field> -->

          <v-spacer></v-spacer>

          <v-responsive max-width="260">
            <v-text-field
              @keypress="search"
              v-model="cityZip"
              density="compact"
              hide-details
              variant="outlined"
            ></v-text-field>
            <!-- <v-text-field class="py-0" density="default" variant="filled"></v-text-field> -->
          </v-responsive>
        </v-container>
      </v-app-bar>
    <!-- </v-app> -->

</template>

<script setup>
import { ref } from "vue";
import { useStore } from '../store/app';

const links = ref([
  'Dashboard',
  'Messages',
  'Profile',
  'Updates',
])

const store = useStore()
const cityZip = ref()

const search = async (e) => {
  if (e.key == "Enter") {
    await store.searchWeather(cityZip.value)
    if (store.error) {
      router.push({ name: "Error" });
    }
    cityZip.value = "";
  }
  console.log(store.recentSearches)
};
</script>

<style>

</style>