<template>
  <!-- <form action="submit"> -->
  <form @submit="onSubmit">
    <label for="">DATE</label
    ><input required type="date" name="date" id="date" v-model="expense.date" />
    <label for="">AMOUNT</label
    ><input
      required
      type="number"
      name="amount"
      id="amount"
      v-model="expense.amount"
    />

    <label for="">SELECT Where</label>
    <select required name="where" id="where" v-model="expense.where">
      <option v-for="item in cats" :key="item.id">
        {{ item.name }}
      </option>S
    </select>

    <label for="">Description</label
    ><input required type="text" name="tags" id="tags" v-model="expense.tags" />

    <label for="">SELECT HOW</label>
    <select required name="how" id="selecthow" v-model="expense.how">
      <option v-for="item in hows" :key="item.id">
        {{ item.name }}
      </option>
    </select>
    <button type="submit">Submit</button>
  </form>
</template>

<script>
export default {
  name: "EditItem",
  props: {
    cats: Array,
    hows: Array,
  },
  data() {
    return {
      expense: {
        date: null,
        amount: null,
        where: null,
        how: null,
        tags: null,
      },
    };
  },
  methods: {
    onSubmit: function (e) {
      e.preventDefault();
      // console.log(this.expense)
     
      this.$emit("add-expense", this.expense);
      this.amount = "";
      this.date = "";
      this.tags = "";
      this.where = "";
      this.how = "";
    },
  },
};
</script>

<style>
</style>
