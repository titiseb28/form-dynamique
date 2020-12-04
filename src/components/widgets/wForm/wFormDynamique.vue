<template>
  <div>
    <v-row justify="center">
      <v-col cols="8">
        <v-form @submit.prevent="displayForm" v-model="valid">
          <formQuestion
            v-for="(question, index) in questions"
            :question="question"
            :key="index"
            :index="index"
            :questions="questions"
          ></formQuestion>
          <v-btn color="success" type="submit" :disabled="!valid">
            Validate
          </v-btn>
          <v-btn color="danger" @click="$refs.form.reset()">
            reset
          </v-btn>
        </v-form>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "formDynamique",
  props: ["questions"],
  components: {
    formQuestion: () => import("./wForm-question"),
  },
  data() {
    return {
      answers: {},
      valid: false,
    };
  },

  methods: {
    displayForm() {
      console.log("display form", this.questions);

      this.questions.forEach((question) => {
        this.answers = Object.assign(this.answers, {
          [question.champName]: question.answer,
        });
      });
      console.log("answers", this.answers);
      this.$emit("sendData", this.answers);
    },
    resetM() {
      this.$refs.form.reset();
    },
  },
};
</script>

<style></style>
