<template>
  <div class="calc">
    <div class="main">
      <input type="text" v-model="op1" @input="result = ''" />
      <input type="number" v-model="op2" @input="result = ''" />
      ={{ result }}
    </div>
    <div class="keyboard">
      <button @click="sum(op1, op2)">+</button>
      <button @click="sub(op1, op2)">-</button>
      <button @click="mult(op1, op2)">*</button>
      <button @click="div(op1, op2)" :disabled="op2 == 0">/</button>
      <button @click="deg(op1, op2)" title="Степень">^</button>
      <button
        @click="divFloor(op1, op2)"
        :disabled="op2 == 0"
        title="Целочисленное деление"
      >
        //
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Calculator',
  data () {
    return {
      op1: 0,
      op2: 0,
      result: ''
    }
  },
  methods: {
    sum (op1, op2) {
      this.result = +op1 + +op2
    },
    sub (op1, op2) {
      this.result = op1 - op2
    },
    mult (op1, op2) {
      this.result = op1 * op2
    },
    div (op1, op2) {
      if (op2 === 0) {
        this.result = 'На ноль делить нельзя'
      } else {
        this.result = op1 / op2
      }
    },
    deg (op1, op2) {
      if (op2 > 0 || op1 === 0) {
        this.result = op1
        for (let i = 1; i < op2; i++) {
          this.result = this.result * op1
        }
      } else {
        this.result = 1
      }
    },
    divFloor (op1, op2) {
      this.result = Math.floor(op1 / op2)
    }
  }
}
</script>
