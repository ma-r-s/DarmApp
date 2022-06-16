<script>
  import Chart from "$lib/Chart.svelte";
  import { onMount } from "svelte";
  let pLuz = {
    series: [
      {
        data: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      },
    ],
    chart: {
      type: "area",
      toolbar: {
        show: false,
      },
    },
  };
  let pTemp = {
    series: [
      {
        data: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      },
    ],
    chart: {
      type: "area",
      toolbar: {
        show: false,
      },
    },
  };
  let pHum = {
    series: [
      {
        data: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      },
    ],
    chart: {
      type: "area",
      toolbar: {
        show: false,
      },
    },
  };
  let pDist = {
    series: [
      {
        data: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      },
    ],
    chart: {
      type: "area",
      toolbar: {
        show: false,
      },
    },
  };
  let pCom = {
    series: [
      {
        data: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      },
    ],
    chart: {
      type: "area",
      toolbar: {
        show: false,
      },
    },
  };
  let pAgua = {
    series: [
      {
        data: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      },
    ],
    chart: {
      type: "area",
      toolbar: {
        show: false,
      },
    },
  };
  onMount(() => {
    async function fetchData() {
      let response = await fetch("http://192.168.4.1:80/data");
      let array = await response.json();
      pLuz = {
        theme: {
          mode: "dark",
          palette: "palette4",
        },
        series: [
          {
            name: "Luz",
            data: array.luz,
          },
        ],
        chart: {
          height: 350,
          type: "area",
          toolbar: {
            show: false,
          },
        },
        dataLabels: {
          enabled: true,
        },
        stroke: {
          curve: "smooth",
        },
        xaxis: {
          type: "category",
          categories: [
            "1s",
            "2s",
            "3s",
            "4s",
            "5s",
            "6s",
            "7s",
            "8s",
            "9s",
            "10s",
          ],
          tickPlacement: "on",
        },

        legend: {
          show: false,
        },
      };
      pHum = {
        theme: {
          mode: "dark",
          palette: "palette5",
        },
        series: [
          {
            name: "Humedad",
            data: array.humedad,
          },
        ],
        chart: {
          height: 350,
          type: "area",
          toolbar: {
            show: false,
          },
        },
        dataLabels: {
          enabled: true,
        },
        stroke: {
          curve: "smooth",
        },
        xaxis: {
          type: "category",
          categories: [
            "1s",
            "2s",
            "3s",
            "4s",
            "5s",
            "6s",
            "7s",
            "8s",
            "9s",
            "10s",
          ],
          tickPlacement: "on",
        },

        legend: {
          show: false,
        },
      };
      pTemp = {
        theme: {
          mode: "dark",
          palette: "palette9",
        },
        series: [
          {
            name: "Temperatura",
            data: array.temperatura,
          },
        ],
        chart: {
          height: 350,
          type: "area",
          toolbar: {
            show: false,
          },
        },
        dataLabels: {
          enabled: true,
        },
        stroke: {
          curve: "smooth",
        },
        xaxis: {
          type: "category",
          categories: [
            "1s",
            "2s",
            "3s",
            "4s",
            "5s",
            "6s",
            "7s",
            "8s",
            "9s",
            "10s",
          ],
          tickPlacement: "on",
        },

        legend: {
          show: false,
        },
      };
      pDist = {
        theme: {
          mode: "dark",
          palette: "palette7",
        },
        series: [
          {
            name: "Distancia",
            data: array.dist2,
          },
        ],
        chart: {
          height: 350,
          type: "area",
          toolbar: {
            show: false,
          },
        },

        stroke: {
          curve: "smooth",
        },
        xaxis: {
          type: "category",
          categories: [
            "1s",
            "2s",
            "3s",
            "4s",
            "5s",
            "6s",
            "7s",
            "8s",
            "9s",
            "10s",
          ],
          tickPlacement: "on",
        },

        legend: {
          show: true,
        },
      };
      pCom = {
        theme: {
          mode: "dark",
          palette: "palette10",
        },
        series: [
          {
            name: "Comida",
            data: array.dist1,
          },
        ],
        chart: {
          height: 350,
          type: "area",
          toolbar: {
            show: false,
          },
        },

        stroke: {
          curve: "smooth",
        },
        xaxis: {
          type: "category",
          categories: [
            "1s",
            "2s",
            "3s",
            "4s",
            "5s",
            "6s",
            "7s",
            "8s",
            "9s",
            "10s",
          ],
          tickPlacement: "on",
        },

        legend: {
          show: true,
        },
      };
      pAgua = {
        theme: {
          mode: "light",
          palette: "palette1",
        },
        series: [
          {
            name: "Agua",
            data: array.dist3,
          },
        ],
        chart: {
          height: 350,
          type: "area",
          toolbar: {
            show: false,
          },
        },

        stroke: {
          curve: "smooth",
        },
        xaxis: {
          type: "category",
          categories: [
            "1s",
            "2s",
            "3s",
            "4s",
            "5s",
            "6s",
            "7s",
            "8s",
            "9s",
            "10s",
          ],
          tickPlacement: "on",
        },

        legend: {
          show: true,
        },
      };
    }
    const interval = setInterval(fetchData, 1000);
    fetchData();
    return () => clearInterval(interval);
  });
</script>

<div class="navbar bg-base-100">
  <div class="flex-1">
    <a class="btn btn-ghost normal-case text-xl" href="/about">DarmApp</a>
  </div>
  <div class="flex-none">
    <ul class="menu menu-horizontal p-0">
      <li><a class="btn m-2" href="/control">Control</a></li>
      <li><a class="btn m-2" href="/ajustes">Ajustes</a></li>
    </ul>
  </div>
</div>

<div class="card card-compact bg-base-200 shadow-xl m-6">
  <Chart options={pLuz} />
  <div class="card-body">
    <h2 class="card-title">Luminosidad</h2>
    <p>Iluminacion de Darma medida en Lumens</p>
    <div class="card-actions justify-end">
      <button class="btn btn-primary">Ver en Darma</button>
    </div>
  </div>
</div>

<div class="card card-compact bg-base-200 shadow-xl m-6">
  <Chart options={pDist} />
  <div class="card-body">
    <h2 class="card-title">Distancia</h2>
    <p>Distancia de Darma medida en centimetros</p>
    <div class="card-actions justify-end">
      <button class="btn btn-primary">Ver en Darma</button>
    </div>
  </div>
</div>

<div class="card card-compact bg-base-200 shadow-xl m-6">
  <Chart options={pCom} />
  <div class="card-body">
    <h2 class="card-title">Comida</h2>
    <p>Comida de Darma medida en gramos</p>
    <div class="card-actions justify-end">
      <button class="btn btn-primary">Ver en Darma</button>
    </div>
  </div>
</div>

<div class="card card-compact bg-base-200 shadow-xl m-6">
  <Chart options={pAgua} />
  <div class="card-body">
    <h2 class="card-title">Agua</h2>
    <p>Agua de Darma medida en mililitros</p>
    <div class="card-actions justify-end">
      <button class="btn btn-primary">Ver en Darma</button>
    </div>
  </div>
</div>

<div class="card card-compact bg-base-200 shadow-xl m-6">
  <Chart options={pTemp} />
  <div class="card-body">
    <h2 class="card-title">Temperatura</h2>
    <p>Temperatura de Darma medida en grados centigrados</p>
    <div class="card-actions justify-end">
      <button class="btn btn-primary">Ver en Darma</button>
    </div>
  </div>
</div>

<div class="card card-compact bg-base-200 shadow-xl m-6">
  <Chart options={pHum} />
  <div class="card-body">
    <h2 class="card-title">Humedad</h2>
    <p>Humedad de Darma medida en porcentaje de saturacion</p>
    <div class="card-actions justify-end">
      <button class="btn btn-primary">Ver en Darma</button>
    </div>
  </div>
</div>
