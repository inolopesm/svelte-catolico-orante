<script lang="ts">
  export let open: boolean = false
</script>

<div class={`fixed inset-0 bg-gray-900 bg-opacity-50 flex justify-center items-center ${open ? "block" : "hidden"}`}>
  <dialog
    class="bg-gray-50 w-4/5 max-w-sm shadow-lg box-content"
    open={open}
  >
    <slot />
  </dialog>
</div>
