<template>
  <div>
    <b-form @submit.prevent="calculate()">
      <b-form-group
        id="no-people"
        label="Number of people"
        label-for="input-1"
        :invalid-feedback="invalidFeedback"
        :valid-feedback="validFeedback"
        :state="state"
      >
        <b-form-input
          type="number"
          id="input-1"
          v-model.number="input"
          :state="state"
          trim
          @input="showResult = false"/>
      </b-form-group>
      <b-button type="submit" variant="primary" :disabled="!state">Calculate</b-button>
    </b-form>
    <div v-if="showResult" class="mt-4">
      Last man standing: {{ result }}
    </div>
  </div>  
</template>

<script>
export default {
  name: 'Problem1',
  data() {
    return {
      input: 0,
      showResult: false,
      result: null
    }
  },
  computed: {
    state() {
      return this.input > 0
    },
    invalidFeedback() {
      if (this.input <= 0) {
        return 'Please enter a number (>0)'
      }
      return ''
    },
    validFeedback() {
      return this.state ? 'Click "Calculate" now!' : ''
    }
  },
  methods: {
    calculate() {
      this.result = this.findLastManStanding(this.input);
      this.showResult = true;
    },
    findLastManStanding(input) {
      const list = [...Array(input).keys()];
      let curr = 0;
      while (list.length > 1) {
        const toKill = (curr < list.length - 1) ? curr + 1 : 0;
        list.splice(toKill, 1);
        if (curr < list.length - 1) {
          curr++;
        } else {
          curr = 0;
        }
      }
      return list[curr] + 1; // index starting from 1
    }
  }
}
</script>
