<template>
  {{ name }}
  <br />
  User - reactive: {{ user.first_name }} {{ user.second_name }}
  <br />
  Admin - ref:
  {{ admin.first_name }} {{ admin.second_name }}
  <br />
  <div>Computed: {{ fullName }}</div>
  <div>
    <button @click="changeName()">Change</button>
  </div>

  <br />
  <br />
  <br />

  <div><h2>Hook</h2></div>
  <AppHook v-if="showAppHook" />
  <div>
    <button @click="showAppHook = !showAppHook">Toggle</button>
  </div>
</template>

<script>
import { reactive, ref, computed, watch } from "vue";
import AppHook from "./components/AppHook.vue";

export default {
  name: "App",
  setup() {
    const user = reactive({
      first_name: "Joao1",
      second_name: "Vitor",
    });
    const admin = ref({
      first_name: "Admin",
      second_name: "Master",
    });
    const fullName = computed(() => {
      return `${admin.value.first_name} ${admin.value.second_name}`;
    });
    watch(
      admin,
      () => {
        console.log("watch: ", admin);
      },
      {
        deep: true,
      }
    );
    let name = "João";
    const changeName = () => {
      name = "Vitor";
      user.first_name = "euuu";
      //Para alterar o obj do red deve se usar o (.value)
      admin.value.first_name = "olaaa";
    };
    // --------

    const showAppHook = ref(true);
    return {
      name,
      admin,
      user,
      changeName,
      fullName,
      showAppHook,
    };
  },
  components: { AppHook },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
