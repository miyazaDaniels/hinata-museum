<template>
  <div>
    <v-container class="pa-4">
      <div class="d-flex flex-wrap">
        <div v-for="work in works" :key="work.id" class="work-column pa-2">
          <WorkItem :work="work"></WorkItem>
        </div>
      </div>
      <div v-if="hasMoreData" v-intersect="onIntersect" class="loading">
        <v-progress-circular v-if="isLoading" indeterminate />
      </div>
    </v-container>
  </div>
</template>

<script>
import { createClient } from "microcms-js-sdk";
import WorkItem from "../components/WorkItem.vue";

const MICROCMS_API_KEY = process.env.VUE_APP_MICROCMS_API_KEY
const FETCH_LIMIT = 10;

export default {
  name: "HomePage",
  components: {
    WorkItem,
  },
  data() {
    return {
      works: [],
      isLoading: false,
      hasMoreData: true,
      offset: 0,
    };
  },
  created() {
    this.client = createClient({
      serviceDomain: "hinata-museum",
      apiKey: MICROCMS_API_KEY,
    });
  },
  methods: {
    updateWorks() {
      this.client
        .get({
          endpoint: "works",
          queries: { offset: this.offset }
        })
        .then((res) => {
          this.works = this.works.concat(res.contents);
          this.isLoading = false;
          this.updateOffset(res.totalCount);
        })
        .catch((err) => {
          console.log(err);
          this.isLoading = false;
          this.offset = 0;
          this.hasMoreData = false;
        });
    },
    updateOffset(totalCount) {
      if (this.offset + FETCH_LIMIT > totalCount) {
        this.hasMoreData = false;
      } else {
        this.offset += FETCH_LIMIT;
      }
    },
    onIntersect(entries, observer, isIntersecting) {
      if (!isIntersecting) {
        return;
      }
      this.isLoading = true;
      this.updateWorks();
    },
  },
};
</script>
<style scoped>
.loading {
  margin: 10px;
  text-align: center;
}

.work-column {
  width: 50%;
}

@media (max-width: 600px) {
  .work-column {
    width: 100%;
  }
}
</style>