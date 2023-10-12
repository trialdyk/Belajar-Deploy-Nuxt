<template>
  <div>
    <Alert
      v-for="list in lists.data"
      :key="list.id"
      @click="deleteAlert(list.id)"
      :list="list"
    />
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      lists: [],
    };
  },
  async created() {
    const response = await axios.get("https://to-do.trialdy.me/api/list");
    this.lists = response.data;
  },
  methods: {
    deleteAlert(id) {
      ElMessageBox.confirm(
        "proxy will permanently delete the file. Continue?",
        "Warning",
        {
          confirmButtonText: "OK",
          cancelButtonText: "Cancel",
          type: "warning",
        }
      )
        .then(() => {
          axios.delete(`https://to-do.trialdy.me/api/list/${id}`)
            .then((response) => {
              ElMessage({
                message: "Sukses, Berhasil Menghapus Data!",
                type: "success",
              });
              this.fetchData();
            })
            .catch((error) => {
              console.error(error);
            });
        })
        .catch(() => {
          ElMessage({
            type: "warning",
            message: "Delete canceled",
          });
        });
    },
    fetchData() {
      // Ambil data terbaru dari API
      axios
        .get("https://to-do.trialdy.me/api/list")
        .then((response) => {
          this.lists = response.data;
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>
