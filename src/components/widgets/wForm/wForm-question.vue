<template>
  <div>
    {{ index }}
    <span v-if="question.type == 'input'">
      <v-text-field
        v-model="answer"
        :label="question.label"
        hide-details="auto"
        :placeholder="question.placeholder"
        @change="changeAnswer(answer, index)"
        :rules="rules"
        v-mask="question.mask"
        :append-icon="question.appendIcon"
        :prepend-icon="question.prependIcon"
        :messages="question.messages"
      ></v-text-field>
    </span>

    <span v-else-if="question.type == 'select'">
      <v-select
        v-model="answer"
        :items="question.options"
        filled
        :label="question.label"
        dense
        :placeholder="question.placeholder"
        @change="changeAnswer(answer, index)"
        :rules="rules"
      ></v-select>
    </span>

    <span v-else-if="question.type == 'radio'">
      <v-radio-group v-model="answer" :rules="rules">
        <v-radio
          v-for="option in question.options"
          :key="option"
          :label="`Radio ${option}`"
          :value="option"
          :placeholder="question.placeholder"
          @click="changeAnswer(answer, index)"
        ></v-radio>
      </v-radio-group>
    </span>

    <span v-else-if="question.type == 'textarea'">
      <v-textarea
        v-model="answer"
        :label="question.label"
        :placeholder="question.placeholder"
        @change="changeAnswer(answer, index)"
        :rules="rules"
      ></v-textarea>
    </span>
    <span v-else-if="question.type == 'checkbox'">
      <v-checkbox
        v-model="answer"
        :label="question.label"
        @change="changeAnswer(answer, index)"
        :rules="rules"
      ></v-checkbox>
    </span>
    <span v-else-if="question.type == 'datepicker'">
      <v-date-picker
        v-model="answer"
        @change="changeAnswer(answer, index)"
        :rules="rules"
      ></v-date-picker>
    </span>

    <span v-else-if="question.type == 'switch'">
      <v-switch
        v-model="answer"
        @change="changeAnswer(answer, index)"
        :rules="rules"
        :label="question.label"
      ></v-switch>
    </span>
  </div>
</template>

<script>
export default {
  name: "form-question",
  props: ["question", "index", "questions"],
  data() {
    return {
      rules: [],
      answer: null,
      required: [(v) => !!v || "Required"],
      email: [
        (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
        (v) => !!v || "Required",
      ],
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      console.log("init");
      if (this.question.rules == "required") {
        this.rules = this.required;
      } else if (this.question.rules == "email") {
        this.rules = this.email;
      }
    },
    changeAnswer(answer, index) {
      console.log("in changeAnswer", index);
      this.questions[index].answer = answer;
    },
  },
};
</script>

<style></style>
