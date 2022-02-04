<template>
  <div v-if="dataloaded" class="beerCard">
    <div class="beerCard__title">
      <strong>Beer for you</strong
      ><button @click="getNewBeer">another beer</button>
    </div>
    <div class="beerCard__data">
      <strong>Brand: </strong>{{ beerData.brand }} <br />
      <strong>Name: </strong>{{ beerData.name }} <br />
      <strong>Style: </strong>{{ beerData.style }} <br />
      <strong>Hop: </strong>{{ beerData.hop }} <br />
      <strong>Yeast: </strong>{{ beerData.yeast }} <br />
      <strong>Malts: </strong>{{ beerData.malts }} <br />
      <strong>Ibu: </strong>{{ beerData.ibu }} <br />
      <strong>Alcohol: </strong>{{ beerData.alcohol }} <br />
      <strong>Blg: </strong>{{ beerData.blg }} <br />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      beerData: null,
      dataloaded: false,
    };
  },
  async created() {
    const response = await fetch(
      "https://random-data-api.com/api/beer/random_beer"
    );
    const data = await response.json();
    this.beerData = data;
    this.dataloaded = true;
  },

  methods: {
    async getNewBeer() {
      const response = await fetch(
        "https://random-data-api.com/api/beer/random_beer"
      );
      const data = await response.json();
      this.beerData = data;
    },
  },
};
</script>

<style scoped lang="scss">
.beerCard {
  background-color: white;
  padding: 10px;
  height: 100%;
  border-radius: 5px;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16), 0 3px 6px rgba(0, 0, 0, 0.23);
  &__title {
    font-size: 16pt;
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    button {
      background: none;
      padding: 5px;
      border-radius: 3px;
      border: 1px solid green;
      cursor: pointer;
    }
  }
  &__data {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    gap: 3px;
  }
}
</style>
