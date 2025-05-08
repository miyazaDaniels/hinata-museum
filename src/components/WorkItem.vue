<template>
  <v-card class="work-item">
    <v-img :src="url" class="work-image"></v-img>
    <v-card v-if="work.caption" class="mt-3 mx-3 mb-2 pa-3 caption">
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
.work-item {
  margin: 8px;
  font-family: 'Kaisei Opti', serif;
}

.work-image {
  width: 100%;
  height: auto;
  object-fit: cover;
}

.caption {
  text-align: center;
}

.title {
  margin: 0;
  font-size: 1.1em;
  font-weight: 500;
  line-height: 1.4;
}

.english-title {
  margin: 4px 0 0;
  font-size: 0.9em;
  font-weight: 400;
  line-height: 1.4;
  color: #666;
}

.creator {
  margin: 8px 0 0;
  font-size: 0.85em;
  font-weight: 400;
  line-height: 1.4;
}

.materials,
.size {
  margin: 4px 0 0;
  font-size: 0.8em;
  line-height: 1.4;
  color: #666;
}

.comment {
  margin: 8px 0 0;
  font-size: 0.85em;
  line-height: 1.6;
  color: #444;
}
</style>
