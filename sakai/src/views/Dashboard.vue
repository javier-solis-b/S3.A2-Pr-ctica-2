<template>
    <div class="grid">
      <div class="col-12 xl:12">
        <div class="card">
          <div class="card-content">
            <div class="card-img">
              <img src="/demo/images/Fondo/Platillo.jpg" alt="Imagen del platillo" width="492" />
              <div class="image-text1">BIENVENIDOS</div>
              <div class="image-text">¡A donde el sabor ideal los hará volver!</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <style scoped>
  .card {
    background: url('/demo/images/Fondo/Platillo.jpg') no-repeat center center;
    background-size: cover;
    height: 100vh;
    position: relative;
  }
  
  .card-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    width: 100%;
    height: 100%;
  }
  
  .card-img {
    position: relative;
    margin-bottom: 20px;
  }
  
  .image-text1 {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -120%);
    background-color: rgba(14, 8, 8, 0.7);
    padding: 10px;
    border-radius: 5px;
    font-size: 20px;
  }
  .image-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -10%);
    background-color: rgba(14, 8, 8, 0.7);
    padding: 10px;
    border-radius: 5px;
    font-size: 18px;
  }
  
  /* Puedes agregar estilos adicionales según tus necesidades */
  </style>
  
  
  <style scoped>
  .card {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    height: 100%; /* Asegura que la tarjeta ocupe toda la altura del contenedor padre */
  }
  
  .card-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    width: 100%;
    height: 100%; /* Asegura que el contenido de la tarjeta esté centrado vertical y horizontalmente */
  }
  
  .card-img {
    margin-bottom: 20px; /* Espacio opcional entre la imagen y el contenido */
  }
  </style>
  
  
  <script setup>
  import { onMounted, ref, watch } from 'vue';
  import ProductService from '@/service/ProductService';
  import { useLayout } from '@/layout/composables/layout';
  
  const { isDarkTheme } = useLayout();
  
  const products = ref(null);
  const lineData = ref({
    datasets: [
      {
        label: 'First Dataset',
        data: [65, 59, 80, 81, 56, 55, 40],
        fill: false,
        backgroundColor: '#2f4860',
        borderColor: '#2f4860',
        tension: 0.4,
      },
      {
        label: 'Second Dataset',
        data: [28, 48, 40, 19, 86, 27, 90],
        fill: false,
        backgroundColor: '#00bb7e',
        borderColor: '#00bb7e',
        tension: 0.4,
      },
    ],
  });
  const items = ref([
    { label: 'Add New', icon: 'pi pi-fw pi-plus' },
    { label: 'Remove', icon: 'pi pi-fw pi-minus' },
  ]);
  const lineOptions = ref(null);
  const productService = new ProductService();
  
  onMounted(() => {
    productService.getProductsSmall().then((data) => (products.value = data));
  });
  
  const formatCurrency = (value) => {
    return value.toLocaleString('en-US', { style: 'currency', currency: 'USD' });
  };
  
  const applyLightTheme = () => {
    lineOptions.value = {
      plugins: {
        legend: {
          labels: {
            color: '#495057',
          },
        },
      },
      scales: {
        x: {
          ticks: {
            color: '#495057',
          },
          grid: {
            color: '#ebedef',
          },
        },
        y: {
          ticks: {
            color: '#495057',
          },
          grid: {
            color: '#ebedef',
          },
        },
      },
    };
  };
  
  const applyDarkTheme = () => {
    lineOptions.value = {
      plugins: {
        legend: {
          labels: {
            color: '#ebedef',
          },
        },
      },
      scales: {
        x: {
          ticks: {
            color: '#ebedef',
          },
          grid: {
            color: 'rgba(160, 167, 181, .3)',
          },
        },
        y: {
          ticks: {
            color: '#ebedef',
          },
          grid: {
            color: 'rgba(160, 167, 181, .3)',
          },
        },
      },
    };
  };
  
  watch(
    isDarkTheme,
    (val) => {
      if (val) {
        applyDarkTheme();
      } else {
        applyLightTheme();
      }
    },
    { immediate: true }
  );
  </script>
  
