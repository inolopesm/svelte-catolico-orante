<script lang="ts">
  let modal = "";

  const openModal = (key: string) => () => {
    modal = key;
  };

  const closeModal = () => {
    modal = "";
  };
</script>

<main class="bg-gray-100 h-screen text-gray-900">
  <section class="bg-gray-50 shadow-md mb-10">
    <div class="container mx-auto p-4">
      <h1 class="text-xl">Católico Orante</h1>
    </div>
  </section>
  <section class="container mx-auto p-4">
    <div class="bg-gray-50 p-4 rounded shadow">
      <h2 class="text-2xl font-bold mb-2">Orações</h2>
      <h3 class="text-lg font-bold mb-2">Comuns</h3>
      <ul class="list-disc list-inside flex flex-col gap-1">
        <li>
          <button
            class="text-blue-400 hover:underline"
            on:click={openModal("ave-maria")}
          >
            Ave Maria
          </button>
        </li>
        <li>
          <button
            class="text-blue-400 hover:underline"
            on:click={openModal("cordeiro-de-deus")}
          >
            Cordeiro de Deus
          </button>
        </li>
        <li>
          <button class="text-blue-400 hover:underline">
            Credo
          </button>
        </li>
        <li>
          <button class="text-blue-400 hover:underline">
            Glória a Deus nas alturas
          </button>
        </li>
        <li>
          <button class="text-blue-400 hover:underline">
            Glória ao Pai
          </button>
        </li>
        <li>
          <button class="text-blue-400 hover:underline">
            Pai Nosso
          </button>
        </li>
        <li>
          <button class="text-blue-400 hover:underline">
            Salve Rainha
          </button>
        </li>
        <li>
          <button class="text-blue-400 hover:underline">
            Santo Anjo
          </button>
        </li>
        <li>
          <button class="text-blue-400 hover:underline">
            Sinal da Cruz
          </button>
        </li>
        <li>
          <button class="text-blue-400 hover:underline">
            Vinde Espírito Santo
          </button>
        </li>
      </ul>
    </div>
  </section>

  <div class={`fixed inset-0 bg-gray-900 bg-opacity-50 flex justify-center items-center ${modal ? "visible" : "invisible"}`}>
    <dialog
      class="bg-gray-50 w-4/5 max-w-sm shadow-lg box-content"
      open={!!modal}
    >
      <div class={modal === "ave-maria" ? "block" : "hidden"}>
        <h2 class="text-2xl font-bold mb-2">Ave Maria</h2>
        <p>
          Ave Maria, cheia de graça, o Senhor é convosco, bendita sois vós entre as
          mulheres e bendito é o fruto do vosso ventre, Jesus. Santa Maria, Mãe de
          Deus, rogai por nós pecadores, agora e na hora da nossa morte. Amém
        </p>
      </div>
      <div class={modal === "cordeiro-de-deus" ? "block" : "hidden"}>
        <h2 class="text-2xl font-bold mb-2">Cordeiro de Deus</h2>
        <p>
          Cordeiro de Deus, que tirais o pecado do mundo, tende piedade de
          nós.<br />
          Cordeiro de Deus, que tirais o pecado do mundo, tende piedade de
          nós.<br />
          Cordeiro de Deus, que tirais o pecado do mundo, dai-nos a paz.
        </p>
      </div>
      <footer class="flex justify-end">
        <button
          class="px-4 py-2 text-blue-400 hover:underline"
          on:click={closeModal}
        >
          Ok
        </button>
      </footer>
    </dialog>
  </div>
</main>
