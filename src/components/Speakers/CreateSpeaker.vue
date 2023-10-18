<template>
  <div class="container">
    <div class="d-flex justify-content-center">
      <form v-on:submit.prevent="createSpeaker"
        class="bg-light border rounded-2 p-3 w-50 position-relative position-absolute top-50 start-50 translate-middle">
        <h2 class="mb-3 fw-bold pt-3 text-center">Create Speaker</h2>
        <hr>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Model: </label>
          <input type="text" v-model="speaker.model" class="form-control" required>
        </div>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Brand: </label>
          <input type="text" v-model="speaker.brand" class="form-control" required>
        </div>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Watt: </label>
          <input type="text" v-model="speaker.watt" class="form-control" required>
        </div>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Power Input: </label>
          <input type="text" v-model="speaker.power_input" class="form-control" required>
        </div>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Status: </label>
          <input type="text" v-model="speaker.status" class="form-control" required>
        </div>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Type: </label>
          <input type="text" v-model="speaker.type" class="form-control" required>
        </div>
        <div class="mb-3 mx-3">
          <button type="submit" class="btn btn-success">Create Speaker</button>
          <button v-on:click="$router.back()" class="btn btn-danger">Back</button>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
import SpeakerService from "@/services/SpeakerService";

export default {
  data() {
    return {
      speaker: {
        model: "",
        brand: "",
        watt: "",
        power_input: "",
        status: "",
        type: ""
      }
    };
  },
  methods: {
    async createSpeaker() {
      try {
        await SpeakerService.post(this.speaker);
        this.$router.push({
          name: "speakers"
        });
      } catch (err) {
        console.log(err);
      }
    }
  }
};
</script>
<style scoped></style>
