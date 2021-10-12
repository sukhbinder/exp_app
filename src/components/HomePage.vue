<template>
  <div>
    <Header></Header>
    <input type="button" value="Add Exp" />
    <EditItem
      @add-expense="addExpense"
      :cats="wherecategories"
      :hows="howcategories"
    />
  </div>

  <div>
    <h1>Category</h1>

    {{ this.wherecategories }}
  </div>

  <h2>How category</h2>
  {{ this.howcategories }}

  <h2>Expense</h2>
  <ListItems :Items="expenses" />
  <div>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from "./Header.vue";
import Footer from "./Footer.vue";
import ListItems from "./ListItems.vue";
import EditItem from "./EditItem.vue";

import axios from "axios";
export default {
  name: "HomePage",
  components: {
    Header,
    Footer,
    ListItems,
    EditItem,
  },
  data() {
    return {
      expenses: [],
      wherecategories: [],
      howcategories: [],
    };
  },
  created() {
    this.getCategory();
    this.getHowCategory();
    this.getExpenses();
  },
  methods: {
    addExpense: function (exp) {
      console.log(exp);
      var exp_where = this.wherecategories.find((x) => x.name === exp.where).id;
      var exp_how = this.howcategories.find((x) => x.name === exp.how).id;
      // console.log(exp_where, exp_how);
      const data = {
        date: exp.date,
        amount: exp.amount,
        where: exp_where,
        how: exp_how,
        tags: exp.tags,
      };
      axios
        .post("http://127.0.0.1:8000/api/expenses/", data, {})
        .then((response) => {
          console.log(response);
          this.getExpenses();
        })
        .catch((error) => {
          console.log(error);
        });
    },
    getCategory: function () {
      var vm = this;
      axios
        .get("http://127.0.0.1:8000/api/cat")
        .then(function (response) {
          console.log(response);
          vm.wherecategories = response.data;
        })
        .catch(function (response) {
          console.log(response);
        });
    },
    getHowCategory: function () {
      var vm = this;
      axios
        .get("http://127.0.0.1:8000/api/how")
        .then(function (response) {
          console.log(response);
          vm.howcategories = response.data;
        })
        .catch(function (response) {
          console.log(response);
        });
    },
    getExpenses: function () {
      var vm = this;
      axios
        .get("http://127.0.0.1:8000/api/expenses/")
        .then(function (response) {
          console.log(response);
          vm.expenses = response.data;
          vm.expenses = vm.expenses.reverse();
        })
        .catch(function (response) {
          console.log(response);
        });
    },
  },
};
</script>

<style>
</style>

