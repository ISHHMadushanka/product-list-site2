<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-lg-12 text-center">
          <h1 class="page-title">Our Product List</h1>
        </div>
        <div class="col-lg-12 mt-5">
          <form action="#" method="post" enctype="multipart/form">
            <div class="row">
              <div class="col-lg-8">
                <div class="form-group">
                  <input class="form-control" name="name" type="text" placeholder="Enter the Product name" required>
                </div>
                <div class="form-group mt-5">
                  <input class="form-control" name="price" type="text" placeholder="Enter the Product Price" required>
                </div>
              </div>
              <div class="col-lg-4">
                <button type="submit" class="btn btn-primary">Submit</button>
              </div>
            </div>
          </form>
        </div>
        <div class="col-lg-12 mt-5 mb-5">
          <div>
            <table class="table table-success table-striped">
              <thead>
                <tr>
                  <th scope="col">Id</th>
                  <th scope="col">Name</th>
                  <th scope="col">Price</th>
                  <th scope="col">Status</th>
                  <!-- <th scope="col">Action</th> -->
                </tr>
              </thead>
              <tbody>
                  <tr v-for="item in items">
                      <td scope="row">{{ item.id }}</td>
                      <td>{{ item.name }}</td>
                      <td>{{ item.price }}</td>
                      <td>
                      <span v-if="item.done == 0" class="badge bg-warning">Inactive</span>
                      <span v-else class="badge bg-success">Active</span>
                      </td>
                  </tr>
              </tbody>
            </table>
          </div>
        </div>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'home',
  layout: 'dashboard',
  data() {
    return {
      items: [],
    }
  },
  methods: {
    getItems() {
      this.$axios.get('api/items').then(response => {
        this.items = response.data;
        console.log(this.items);
      });
    },

  },
  mounted() {
    this.getItems();
  },

}
</script>

<style>
 .page-title {
            padding-top: 5vh;
            font-size: 3rem;
            color: #81867e;
        }

</style>
