<template>
  <div id="app" class="container">
    <!-- Heading -->
    <h1>Daftar Pengguna Baru</h1>

    <!-- Form Section -->
    <section class="form-section">
      <form @submit.prevent="submitForm">
        <div class="form-group">
          <input type="text" v-model="name" placeholder="Masukkan Nama" required />
        </div>
        <div class="form-group">
          <input type="email" v-model="email" placeholder="Masukkan Email" required />
        </div>
        <button type="submit" class="submit-btn">Kirim</button>
      </form>
    </section>

    <!-- Table Section -->
    <section class="table-section" v-if="users.length">
      <h2>Daftar Pengguna</h2>
      <table>
        <thead>
          <tr>
            <th>Nama</th>
            <th>Email</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(user, index) in users" :key="index">
            <td>{{ user.name }}</td>
            <td>{{ user.email }}</td>
          </tr>
        </tbody>
      </table>
    </section>

    <!-- Link Section -->
    <section class="link-section">
      <a href="https://vuejs.org/" target="_blank">Pelajari lebih lanjut tentang Vue.js</a>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      users: [],
    };
  },
  methods: {
    submitForm() {
      this.users.push({
        name: this.name,
        email: this.email,
      });
      this.name = '';
      this.email = '';
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
  text-align: center;
}

h1 {
  color: #333;
  margin-bottom: 20px;
}

.form-section {
  margin-bottom: 30px;
}

.form-group {
  margin-bottom: 15px;
}

.form-group input {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
}

.submit-btn {
  padding: 10px 20px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.submit-btn:hover {
  background-color: #369970;
}

.table-section {
  margin-top: 20px;
}

table {
  width: 100%;
  border-collapse: collapse;
}

table th, table td {
  padding: 10px;
  border: 1px solid #ddd;
}

table th {
  background-color: #f4f4f4;
}

.link-section a {
  color: #42b983;
  font-weight: bold;
  text-decoration: none;
}

.link-section a:hover {
  text-decoration: underline;
}
</style>
