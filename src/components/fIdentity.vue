<template>
  <div>
    <formDynamique :questions="listIdentity" v-on:sendData="dataForm" />
    
  </div>
</template>

<script>
export default {
  name: "fIdentity",
  components: {
    formDynamique: () => import("./widgets/wForm/wFormDynamique"),
  },
  data() {
    return {
      listIdentity: [
        {
          id: 1,
          label: "First Name",
          type: "input",
          champName: "firstName",
          appendIcon: "mdi-phone",
          prependIcon: "mdi-phone",
          messages: "Messasssges",
          // rules: "required",
        },
        {
          id: 2,
          label: "Last Name",
          type: "input",
          champName: "lastName",
        },
        {
          id: 3,
          label: "Email",
          type: "input",
          champName: "email",
          // rules: "email",
        },
        {
          id: 4,
          label: "Job",
          type: "select",
          options: ["...", "Developer", "Ops", "Project Manager"],
          champName: "job",
          // rules: "required",
        },
        {
          id: 5,
          label: "Gender",
          type: "radio",
          options: ["Male", "Female"],
          champName: "gender",
          // rules: "required",
        },
        {
          id: 6,
          label: "Address",
          type: "textarea",
          placeholder: "Your zip code and city",
          champName: "adress",
          // rules: "required",
        },
        {
          id: 7,
          label: "Phone Number",
          type: "input",
          champName: "phone",
          // rules: "required",
          mask: "## ## ## ## ##",
        },
        {
          id: 8,
          label: "cgv",
          type: "switch",
          champName: "cgv",
        },
        {
          id: 9,
          label: "date",
          type: "datepicker",
          champName: "date",
          rules: "required",
        },
      ],
    };
  },
  methods: {
    dataForm(value) {
      console.log("in valid", value);
    },
  },
};
</script>

<style scoped></style>
