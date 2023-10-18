<template>
  <div class="container">
    <h2 class="mb-3 fw-bold pt-3">Get All Speakers</h2>
        <h4 class="mb-3 fw-bold">Speaker Amount: {{ speakers.length }}</h4>
        <button class="btn btn-warning mb-3 fw-bold" v-on:click="navigateTo('/speaker/create/')">Create Speaker</button>
        <div class="row row-cols-2 d-flex justify-content-center fw-bold">
            <div v-for="speaker in speakers" v-bind:key="speaker.id" style="width: 40rem"
                class="col border mb-3 mx-2 p-3 text-start bg-light rounded-2">
                <div class="row p-2 mb-3">
                    <div class="col-3">
                        <label for="brand" class="form-label">ID:</label>
                        <span class="input-group-text"> {{ speaker.id }} </span>
                    </div>
                    <div class="col">
                        <label for="product" class="form-label">Model:</label>
                        <span class="input-group-text"> {{ speaker.model }} </span>
                    </div>
                </div>
                <div class="row p-2 mb-3">
                    <div class="col">
                        <label for="color" class="form-label">Brand:</label>
                        <span class="input-group-text"> {{ speaker.brand }} </span>
                    </div>
                    <div class="col">
                        <label for="color" class="form-label">Watt:</label>
                        <span class="input-group-text"> {{ speaker.watt }} </span>
                    </div>
                </div>
                <div class="row p-2 mb-3">
                    <div class="col">
                        <label for="color" class="form-label">Power Input:</label>
                        <span class="input-group-text"> {{ speaker.power_input }} </span>
                    </div>
                    <div class="col">
                        <label for="color" class="form-label">Status:</label>
                        <span class="input-group-text"> {{ speaker.status }} </span>
                    </div>
                </div>
                <button class="btn btn-primary" v-on:click="navigateTo('/speaker/' + speaker.id)">View</button>
                <div class="float-end">
                    <button class="btn btn-success" v-on:click="navigateTo('/speaker/edit/' + speaker.id)">Edit</button>
                    <button class="btn btn-danger" v-on:click="deleteComputer(speaker)">Delete</button>
                </div>
            </div>
        </div>
  </div>
</template>
<script>
import SpeakerServices from "@/services/SpeakerService";
export default {
  data() {
    return {
      speakers: []
    };
  },
  methods: {
    navigateTo(route) {
      this.$router.push(route);
    },
    async deleteUser(speaker) {
      let result = confirm("Want to delete?");
      if (result) {
        try {
          await SpeakerServices.delete(speaker);
          this.refreshData()
        } catch (err) {
          console.log(err);
        }
      }
    },
    async refreshData() {
      this.speakers = (await SpeakerServices.index()).data;
    }
  },
  async created() {
    this.speakers = (await SpeakerServices.index()).data;
  }
};
</script>
<style scoped></style>
