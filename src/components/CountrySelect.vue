<template>
  <select
    @change="onChange"
    class="form-select mt-1 block w-full border p-3 rounded mt-10"
    v-model="selected"
  >
    <option value="0">Select Country</option>
    <option v-for="country in countries" :key="country.ID" :value="country.ID">
      {{ country.Country }}
    </option>
  </select>
</template>

<script>
export default {
  name: "CountrySelect",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find(
        (country) => country.ID === this.selected
      );
      console.log(country);
      this.$emit("get-country", country);
    },
  },
};
</script>