<script lang="ts">
  import '@skeletonlabs/skeleton/themes/theme-skeleton.css';
  import '@skeletonlabs/skeleton/styles/skeleton.css';
  import '../app.postcss';

  import { AppShell } from '@skeletonlabs/skeleton';
  import { navigating } from '$app/stores';
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';
  import LoadingSpinner from '$lib/components/LoadingSpinner.svelte';
</script>

<AppShell>
  <svelte:fragment slot="header">
    <Header />
  </svelte:fragment>

  {#if $navigating}
    <div class="fixed inset-0 z-[15] bg-black opacity-60">
      <div class="flex justify-center items-center w-full h-full">
        <LoadingSpinner />
      </div>
    </div>
  {/if}

  <div class="container mx-auto max-w-4xl p-4 space-y-8 mt-4 h-full">
    <slot />
  </div>

  <svelte:fragment slot="footer">
    <hr />

    <Footer />
  </svelte:fragment>
</AppShell>
