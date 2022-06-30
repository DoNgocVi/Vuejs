<template>
  <div class="container">
    <div class="row">
      <div class="col-md-6 offset-md-3">
        <h2>Add City</h2>
        <form @submit.prevent="onSubmit">
          <div class="form-group">
            <input
              type="text"
              class="form-control mb-2"
              aria-describedby="emailHelp"
              placeholder="Change"
              v-model="name"
            />
          </div>
          <div class="form-group">
            <input
              type="text"
              class="form-control mb-2"
              id="exampleInputEmail1"
              aria-describedby="emailHelp"
              placeholder="Enter email"
              v-model="county"
            />
          </div>
          <div class="form-group">
            <input
              type="text"
              class="form-control mb-2"
              placeholder="Country"
              v-model="country"
            />
          </div>
          <button type="submit" class="btn btn-primary">Submit</button>
        </form>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: null,
      county: null,
      country: null,
    };
  },
  methods: {
    onSubmit() {
      this.$store.dispatch("createCity", {
        data: this.$data,
        router: this.$route,
      });
    },
  },
};
</script>