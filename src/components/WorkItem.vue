<template>
  <v-card>
    <v-img :src="url"></v-img>
    <v-card v-if="work.caption" class="mt-3 mx-3 mb-2 pa-2 caption">
      <div v-if="work.title" class="mb-2">
        <p v-if="work.title" class="title">{{ work.title }}</p>
        <p v-if="work.englishTitle" class="english-title">
          {{ work.englishTitle }}
        </p>
      </div>
      <v-spacer></v-spacer>
      <p v-if="creator" class="creator">{{ creator }}</p>
      <p v-if="work.materials" class="materials">{{ work.materials[0] }}</p>
      <p v-if="work.size" class="size">{{ work.size }}</p>
      <p v-if="work.comment" class="comment">{{ work.comment }}</p>
    </v-card>
    <div role="spacer" v-if="work.caption" class="pb-1"></div>
  </v-card>
</template>

<script>
export default {
  props: {
    work: Object,
  },
  computed: {
    url() {
      return this.work.work.url + "?q=75&fm=webp&fit=clip&w=300&h=300";
    },
    creator() {
      return this.work.creator.join(" ");
    },
  },
};
</script>

<style scoped>
.caption {
  text-align: center;
}

.title {
  margin: 0;
  font-size: 0.9em;
}

.creator,
.comment {
  margin: 0;
  font-size: 0.7em;
}
.materials,
.size {
  margin: 0;
  font-size: 0.65em;
  line-height: normal;
}
</style>
