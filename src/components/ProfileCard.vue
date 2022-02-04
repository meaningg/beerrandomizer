<template>
  <div v-if="dataloaded" class="profileCard">
    <div class="profileCard__title">
      <strong>Profile:</strong> {{ userData.email }}
    </div>
    <div class="profileCard__data">
      <strong>Fist name:</strong> {{ userData.first_name }} <br />
      <strong>Last name:</strong> {{ userData.last_name }} <br />
      <strong>Username:</strong> {{ userData.username }} <br />
      <strong>Gender:</strong> {{ userData.gender }} <br />
      <strong>Phone number:</strong> {{ userData.phone_number }} <br />
      <strong>SIN:</strong> {{ userData.social_insurance_number }} <br />
      <strong>Date of birth:</strong> {{ userData.date_of_birth }} <br />
    </div>
    <div class="profileCard__title">
      <strong>Employment</strong>
    </div>
    <div class="profileCard__data">
      <strong>{{ userData.employment.title }}</strong> <br />
      <strong>Skill: </strong>{{ userData.employment.key_skill }}
    </div>
    <div class="profileCard__title">
      <strong>Adress</strong>
    </div>
    <div class="profileCard__data">
      <strong>City: </strong>{{ userData.address.city }} <br />
      <strong>Street name: </strong>{{ userData.address.street_name }} <br />
      <strong>Street address: </strong>{{ userData.address.street_address }}
      <br />
      <strong>Zip code: </strong>{{ userData.address.zip_code }} <br />
      <strong>State: </strong>{{ userData.address.state }} <br />
      <strong>Country: </strong>{{ userData.address.country }} <br />
      <strong>Coordinates: </strong><br />{{
        userData.address.coordinates.lat
      }},
      <br />
      {{ userData.address.coordinates.lng }} <br />
      <div class="profileCard__title">
        <strong>Credit card</strong>
      </div>
      <div class="profileCard__data">
        <strong>Number: </strong>{{ userData.credit_card.cc_number }} <br />
      </div>
      <div class="profileCard__title">
        <strong>Subscription</strong>
      </div>
      <div class="profileCard__data">
        <strong>Plan: </strong>{{ userData.subscription.plan }} <br />
        <strong>Status: </strong>{{ userData.subscription.status }} <br />
        <strong>Payment method: </strong
        >{{ userData.subscription.payment_method }} <br />
        <strong>Term: </strong>{{ userData.subscription.term }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userData: null,
      dataloaded: false,
    };
  },
  async created() {
    const response = await fetch(
      "https://random-data-api.com/api/users/random_user"
    );
    const data = await response.json();
    this.userData = data;
    this.dataloaded = true;
  },

  methods: {},
};
</script>

<style scoped lang="scss">
.profileCard {
  background-color: white;
  padding: 10px;
  height: 100%;
  border-radius: 5px;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16), 0 3px 6px rgba(0, 0, 0, 0.23);
  &__title {
    font-size: 16pt;
  }
  &__data {
    padding: 5px;
  }
}
</style>
