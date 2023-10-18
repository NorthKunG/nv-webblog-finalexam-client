<template>
  <div class="container">
    <div class="d-flex justify-content-center">
      <form v-on:submit.prevent=""
        class="bg-light border rounded-2 p-3 w-50 position-relative position-absolute top-50 start-50 translate-middle">
        <h2 class="mb-3 fw-bold pt-3 text-center">Speaker</h2>
        <hr>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Model: </label>
          <span class="form-control">{{ speaker.model }}</span>
        </div>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Brand: </label>
          <span class="form-control">{{ speaker.brand }}</span>
        </div>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Watt: </label>
          <span class="form-control">{{ speaker.watt }}</span>
        </div>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Power Input: </label>
          <span class="form-control">{{ speaker.power_input }}</span>
        </div>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Status: </label>
          <span class="form-control">{{ speaker.status }}</span>
        </div>
        <div class="mb-3 mx-3">
          <label for="" class="form-label">Type: </label>
          <span class="form-control">{{ speaker.type }}</span>
        </div>
        <div class="mb-3 mx-3">
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
      speaker: null
    };
  },
  async created() {
    let speakerId = this.$route.params.speakerId;
    this.speaker = (await SpeakerService.show(speakerId)).data
    console.log(this.speakerId)
  }
};
</script>
<style scoped></style>
