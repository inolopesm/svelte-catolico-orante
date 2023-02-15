<script lang="ts">
  import type { ComponentType } from "svelte";
  import Header from "./components/Header.svelte";
  import Link from "./components/Link.svelte";
  import AveMaria from "./components/prayers/AveMaria.svelte";
  import CordeiroDeDeus from "./components/prayers/CordeiroDeDeus.svelte";
  import Credo from "./components/prayers/Credo.svelte";
  import GloriaAoPai from "./components/prayers/GloriaAoPai.svelte";
  import GloriaDeusNasAlturas from "./components/prayers/GloriaDeusNasAlturas.svelte";
  import PaiNosso from "./components/prayers/PaiNosso.svelte";
  import SalveRainha from "./components/prayers/SalveRainha.svelte";
  import SantoAnjo from "./components/prayers/SantoAnjo.svelte";
  import SinalDaCruz from "./components/prayers/SinalDaCruz.svelte";
  import VindeEspiritoSanto from "./components/prayers/VindeEspiritoSanto.svelte";

  type Prayer = {
    label: string;
    Component: ComponentType;
  };

  const prayers: Prayer[] = [
    { label: "Ave Maria", Component: AveMaria },
    { label: "Cordeiro de Deus", Component: CordeiroDeDeus },
    { label: "Credo", Component: Credo },
    { label: "Gloria a Deus nas alturas", Component: GloriaDeusNasAlturas },
    { label: "Glória ao Pai", Component: GloriaAoPai },
    { label: "Pai Nosso", Component: PaiNosso },
    { label: "Salve Rainha", Component: SalveRainha },
    { label: "Santo Anjo", Component: SantoAnjo },
    { label: "Sinal da Cruz", Component: SinalDaCruz },
    { label: "Vinde Espírito Santo", Component: VindeEspiritoSanto },
  ];

  let selectedPrayer: Prayer | null = null;

  const openPrayerModal = (prayer: Prayer) => () => {
    selectedPrayer = prayer;
  };

  const closePrayerModal = () => {
    selectedPrayer = null;
  };
</script>

<main class="bg-gray-100 h-screen text-gray-900">
  <Header />
  <section class="container mx-auto p-4">
    <div class="bg-gray-50 p-4 rounded shadow">
      <h2 class="text-2xl font-bold mb-2">Orações</h2>
      <h3 class="text-lg font-bold mb-2">Comuns</h3>
      <ul class="list-disc list-inside flex flex-col gap-1">
        {#each prayers as prayer}
          <li>
            <Link on:click={openPrayerModal(prayer)}>
              {prayer.label}
            </Link>
          </li>
        {/each}
      </ul>
    </div>
  </section>

  <div class={`fixed inset-0 bg-gray-900 bg-opacity-50 flex justify-center items-center ${selectedPrayer ? "visible" : "invisible"}`}>
    <dialog
      class="bg-gray-50 w-4/5 max-w-sm shadow-lg box-content"
      open={!!selectedPrayer}
    >
      {#each prayers as { label, Component }}
        <Component class={selectedPrayer?.label === label ? "block" : "hidden"} />
      {/each}
      <footer class="flex justify-end">
        <button
          class="px-4 py-2 text-blue-400 hover:underline"
          on:click={closePrayerModal}
        >
          Ok
        </button>
      </footer>
    </dialog>
  </div>
</main>
