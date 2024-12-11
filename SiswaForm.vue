<template>
    <div class="siswa-form-container">
      <form @submit.prevent="addSiswa" class="siswa-form">
        <label for="nama">Nama:</label>
        <input id="nama" v-model="form.nama" type="text" placeholder="Masukkan Nama" />
  
        <label for="usia">Usia:</label>
        <input id="usia" v-model="form.usia" type="number" placeholder="Masukkan Usia" />
  
        <div class="gender-inputs">
          <label>Gender:</label>
          <select id="Gender" v-model="form.gender">
          <option value="">Pilih Gender</option>
          <option value="Laki-laki">Laki-laki</option>
          <option value="Perempuan">Perempuan</option>
        </select>
        </div>
  
        <label for="kelas">Kelas:</label>
        <select id="kelas" v-model="form.kelas">
          <option value="">Pilih Kelas</option>
          <option value="10">10</option>
          <option value="11">11</option>
          <option value="12">12</option>
        </select>
  
        <button type="submit">Tambah Siswa</button>
      </form>
  
      <div class="current-data">
        <h2>Data yang Sedang Diinput:</h2>
        <p>Nama: {{ form.nama }}</p>
        <p>Usia: {{ form.usia }}</p>
        <p>Gender: {{ form.gender }}</p>
        <p>Kelas: {{ form.kelas }}</p>
      </div>
  
      <div class="siswa-list">
        <h2>Daftar Siswa:</h2>
        <ul>
          <li v-for="(siswa, index) in siswaList" :key="index">
            <p>Nama: {{ siswa.nama }}</p>
            <p>Usia: {{ siswa.usia }}</p>
            <p>Gender: {{ siswa.gender }}</p>
            <p>Kelas: {{ siswa.kelas }}</p>
          </li>
        </ul>
      </div>
    </div>
  </template>
  
  <script setup>
  import { reactive, ref } from 'vue';
  
  const form = reactive({
    nama: '',
    usia: null,
    gender: '',
    kelas: ''
  });
  
  const siswaList = ref([]);
  
  const addSiswa = () => {
    if (form.nama && form.usia && form.gender && form.kelas) {
      siswaList.value.push({ ...form });
      form.nama = '';
      form.usia = null;
      form.gender = '';
      form.kelas = '';
    } else {
      alert('Harap isi semua data siswa!');
    }
  };
  </script>
  
  <style scoped></style>