<script setup>
import { reactive } from "vue";

const state = reactive({
  num1: 0,
  num2: 0,
  result: 0,
  operation: "sum",
});

const calculate = () => {
  const { num1, num2, operation } = state;

  switch (operation) {
    case "sum":
      state.result = num1 + num2;
      break;
    case "sub":
      state.result = num1 - num2;
      break;
    case "mul":
      state.result = num1 * num2;
      break;
    case "div":
      state.result = num1 / num2;
      break;
  }
};
</script>

<template>
  <form class="">
    <div class="row">
      <div class="col-md-2">
        <input
          class="form-control"
          type="number"
          v-model="state.num1"
          @input="calculate"
        />
      </div>
      <div class="col-md-1">
        <select
          class="form-control"
          v-model="state.operation"
          @change="calculate"
        >
          <option value="sum">+</option>
          <option value="sub">-</option>
          <option value="mul">*</option>
          <option value="div">/</option>
        </select>
      </div>
      <div class="col-md-2">
        <input
          class="form-control"
          type="number"
          v-model="state.num2"
          @input="calculate"
        />
      </div>
      <div class="col-sm-8 col-md-2">
        <div class="form-control">Resultado: {{ state.result }}</div>
      </div>
    </div>
  </form>
</template>
