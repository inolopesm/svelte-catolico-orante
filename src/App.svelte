<script lang="ts">
  import Button from "./components/Button.svelte";
  import Dialog from "./components/Dialog.svelte";
  import DialogActions from "./components/DialogActions.svelte";
  import DialogTitle from "./components/DialogTitle.svelte";
  import Header from "./components/Header.svelte";
  import ButtonLink from "./components/ButtonLink.svelte";
  import prayers from "./data/prayers.json";
  import DialogContent from "./components/DialogContent.svelte";
  import type { Unpack } from "./utils/typescript"
  import Footer from "./components/Footer.svelte";

  type Prayer = Unpack<typeof prayers>;

  let selectedPrayer: Prayer | null = null;
</script>

<main class="bg-gray-100 h-screen text-gray-900 flex flex-col">
  <Header />
  <section class="container mx-auto p-4 grow">
    <div class="bg-gray-50 p-4 rounded shadow">
      <h2 class="text-2xl font-bold mb-2">Orações</h2>
      <h3 class="text-lg font-bold mb-2">Comuns</h3>
      <ul class="list-disc list-inside flex flex-col gap-1">
        {#each prayers as prayer}
          <li>
            <ButtonLink on:click={() => { selectedPrayer = prayer }}>
              {prayer.label}
            </ButtonLink>
          </li>
        {/each}
      </ul>
    </div>
  </section>
  <Footer />

  {#if selectedPrayer !== null}
    <Dialog open>
      <DialogTitle>
        {selectedPrayer.label}
      </DialogTitle>
      <DialogContent>
        {@html selectedPrayer.content}
      </DialogContent>
      <DialogActions>
        <Button on:click={() => { selectedPrayer = null }}>
          Ok
        </Button>
      </DialogActions>
    </Dialog>
  {/if}
</main>
