<script>
  let ang = 26;
  let com = 0;
  let agu = 0;
  async function postServo() {
    const res = await fetch("http://192.168.4.1/servo", {
      method: "POST",
      body: JSON.stringify({
        ang,
      }),
    });

    const json = await res.json();
    console.log(JSON.stringify(json));
  }
  async function comer() {
    ang = 0;

    const res = await fetch("http://192.168.4.1/comer", {
      method: "POST",
      body: JSON.stringify({
        com,
      }),
    });
    com++;
    const json = await res.json();
    console.log(JSON.stringify(json));
  }
  async function agua() {
    const res = await fetch("http://192.168.4.1/agua", {
      method: "POST",
      body: JSON.stringify({
        agu,
      }),
    });
    agu++;
    const json = await res.json();
    console.log(JSON.stringify(json));
  }
</script>

<div class="navbar bg-base-100">
  <div class="flex-1">
    <a class="btn btn-ghost normal-case text-xl" href="/about">DarmApp</a>
  </div>
  <div class="flex-none">
    <ul class="menu menu-horizontal p-0">
      <li><a class="btn m-2" href="/">Datos</a></li>
      <li><a class="btn m-2" href="/ajustes">Ajustes</a></li>
    </ul>
  </div>
</div>

<div class="flex h-screen">
  <div class="mx-auto">
    <div class="w-96">
      <h1 class="text-center text-4xl font-bold my-3">Compuerta</h1>
      <input
        type="range"
        on:change={postServo}
        min="0"
        max="24"
        bind:value={ang}
        class="range"
      />
    </div>
    <div class="flex justify-around my-9">
      <button on:click={comer} class="btn btn-info">Servir comida: {com}</button
      >
      <button on:click={agua} class="btn btn-success">Servir agua: {agu}</button
      >
    </div>
  </div>
</div>
