<template>
  <div>
    <v-container>
      <v-row dense>
        <v-col v-for="work in works" :key="work.id" class="py-1">
          <WorkItem :work="work"></WorkItem>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import { createClient } from "microcms-js-sdk";
import WorkItem from "../components/WorkItem.vue";

export default {
  name: "HomePage",
  components: {
    WorkItem,
  },
  data() {
    return {
      works: [],
    };
  },
  created() {
    this.client = createClient({
      serviceDomain: "hinata-museum",
      apiKey: "fb80446547044911b4e4273a2034314f0820",
    });
  },
  mounted() {
    this.updateWorks();
  },
  methods: {
    updateWorks() {
      this.client
        .get({
          endpoint: "works",
        })
        .then((res) => {
          console.log(res);
          this.works = res.contents;
        });
    },
  },
};
</script>
