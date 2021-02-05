<template>

  <div v-on:click="getInfo(cInfo)" :class="{ ['card ' + cInfo.id] : true}">
    <div class="card_image"><img :alt="cInfo.id" :src="cInfo.image"/></div>
    <div class="card_title title-white">
      <p>{{ cInfo.name }}</p>
    </div>
  </div>


</template>

<script>
export default {
  name: 'Card',
  props: {
    msg: String,
    cInfo: Object,

  },
  methods: {
    getInfo: (info) => {
      const person = {
        'id': info.id,
        'name': info.name,
        'gender': info.gender,
        'location': info.location.name,
        'species': info.species
      }
      console.log(person)
    }
  }
}
</script>

