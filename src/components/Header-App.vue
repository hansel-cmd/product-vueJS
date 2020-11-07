<template>
 <div class="upperbar">
    <div class="title">
        <h1>LazaPEE</h1>
    </div>
     <div class="searchbar">
        <input type="text" name="searchbar" id="search" placeholder="Search with the Product's Name" v-model="searchName" v-on:keyup="passToParent()"/>
    </div>
</div>
</template>

<script>
export default {
  name: 'Header-App',
  data() {
      return {
          searchName: "",
      }
  },
  methods: {
      passToParent() {
        //   console.log(this.searchName);
          this.$emit('filter-items', this.searchName);
      }
  },
  computed: {

  }
}
</script>

