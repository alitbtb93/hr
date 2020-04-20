<template>
  <v-card class="pb-5 pt-10 px-10 mt-5">
    <v-row>
      <v-col cols="12" md="9">
        <v-text-field
          @input="$v.step.$touch"
          :error-messages="errorMessages"
          v-model="step"
          label="Step"
          outlined
        ></v-text-field>
      </v-col>
      <v-col cols="12" md="3">
        <v-btn
          :disabled="$v.$invalid"
          @click="addCounter"
          height="56px"
          block
          class="primary"
        >Add counter</v-btn>
      </v-col>
    </v-row>
  </v-card>
</template>



<script>
import { required, decimal } from "vuelidate/lib/validators";
// custom validation to ignore float with more than one decimal
var customValidation = value => {
  let stringValue = value.toString();
  if (stringValue.includes(".")) {
    let valueLength = stringValue.length;
    let decimalIndex = stringValue.indexOf(".") + 1;
    let decimalPart = stringValue.slice(decimalIndex, valueLength);
    if (decimalPart.length > 1 ) {
      return false;
    } else {
      return true;
    }
  }
  return true;
};
export default {
  data() {
    return {
      // data variable for binding to text input
      step: null,
      // an array data variable to hold every counter object
      counters: []
    };
  },
  methods: {
    addCounter() {
        this.counters.push({
            step: parseFloat(this.step),
            value:parseFloat(0)
        })
        this.$emit("counters",this.counters)
    }
  },
  computed: {
    errorMessages() {
      const errors = [];
      if (!this.$v.step.$dirty) return errors;
      !this.$v.step.required && errors.push("You must enter a step first.");
      !this.$v.step.decimal &&
        errors.push(
          "Step should be negative or positive integers or ﬂoats with one decimal"
        );
      !this.$v.step.customValidation &&
        errors.push(
          "Step should be negative or positive integers or ﬂoats with one decimal"
        );
      return errors;
    }
  },
  validations: {
    step: {
      required,
      decimal,
      customValidation
    }
  }
};
</script>

<style scoped>
</style>