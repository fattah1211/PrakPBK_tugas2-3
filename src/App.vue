<template>
  <div class="container">
    <h1 class="title">Welcome to Perkebunan Sawit Fattah</h1>
    <!-- Declarative Rendering-->
    <div class="section">
      <h2>Informasi tentang kebun</h2>
      <div class="card">
        <div><span class="label">Jenis bibit:</span> {{ jenis }}</div>
        <div><span class="label">Produksi Bulan Ini:</span> {{ produksi }} ton</div>
      </div>
    </div>
    <!-- Attribute Bindings-->
    <div class="section">
      <h2>Status Kebun</h2>
      <div class="card">
        <div :class="['status', status === 'Aktif' ? 'aktif' : 'nonaktif']">
          Status: {{ status }}
        </div>
        <!-- Event Listeners-->
        <button @click="ubahStatus">Ubah Status</button>
      </div>
    </div>
    <div class="section">
      <h2>Produksi</h2>
      <div class="card">
        <div>Produksi minggu ini: {{ produksi }} ton</div>
        <button @click="tambahProduksi">Tambah 5 Ton</button>
      </div>
    </div>
    <!-- Form Bindings-->
    <div class="section">
      <h2>Ubah Jenis bibit</h2>
      <input type="text" v-model="jenis" placeholder="Masukkan jenis bibit sawit...." />
    </div>
    <!--Conditional Rendering-->
    <div v-if="produksi < 50" class="warning">
      ⚠️ Produksi rendah! Harap cek kondisi kebun dan berikan segera pupuk.
    </div>
  </div>
</template>

<script>
export default {
  name: "DashboardSawit",
  data() {
    return {
      jenis: "varietas",
      produksi: 30,
      status: "Aktif"
    };
  },
  methods: {
    ubahStatus() {
      this.status = this.status === "Aktif" ? "Nonaktif" : "Aktif";
    },
    tambahProduksi() {
      this.produksi += 5;
    }
  }
};
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
  overflow: hidden;
  height: 100%;
  background-color: rgb(184, 234, 196);
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
}
.container {
  max-width: 700px;
  margin: 40px auto;
  padding: 30px;
  background: #92f498;
  border-radius: 16px;
}
.title {
  text-align: center;
  color: #141514;
  font-size: 28px;
  font-weight: bold;
}
.section {
  margin-bottom: 30px;
}
.section h2 {
  margin-bottom: 10px;
  color: #333;
  font-size: 20px;
  border-left: 4px solid #37b13b;
  padding-left: 6px;
}
.card {
  background: #f1f4f1;
  padding: 16px;
  border-radius: 10px;
  margin-bottom: 10px;
}
.label {
  font-weight: bold;
  margin-right: 5px;
  color: #555;
}
.status.aktif {
  color: green;
  font-weight: bold;
}
.status.nonaktif {
  color: red;
  font-weight: bold;
}
button {
  background-color: #37ab3b;
  color: black;
  border: none;
  padding: 10px 18px;
  border-radius: 8px;
  cursor: pointer;
  margin-top: 10px;
  font-weight: 600;
}
button:hover {
  background-color: #388e3c;
}
input[type="text"] {
  padding: 10px;
  width: 100%;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-sizing: border-box;
  margin-top: 8px;
}
.warning {
  background-color: #ffebee;
  color: #b71c1c;
  padding: 12px;
  border-radius: 8px;
  border-left: 4px solid #c62828;
  margin-top: 10px;
}
</style>
