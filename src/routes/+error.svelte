<script>
    import { page } from '$app/stores';
</script>

<svelte:head>
    <title>Errore {$page.status} | DR. Francesco Latanza</title>
</svelte:head>

<!-- flex-grow espande il contenitore nello spazio disponibile del <main>; items-center centra la card verticalmente -->
<div class="w-full flex-grow flex items-center justify-center px-5 py-10 bg-gray-50/50">

    <div class="w-full max-w-[650px] text-center bg-white p-12 md:p-16 rounded-[2.5rem] shadow-[0_20px_60px_-15px_rgba(13,94,86,0.12)] border border-gray-100">

        <div class="w-24 h-24 mx-auto bg-[#0D5E56]/5 rounded-full flex items-center justify-center text-[#0D5E56] mb-8">
            {#if $page.status === 404}
                <svg width="44" height="44" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><polygon points="16.24 7.76 14.12 14.12 7.76 16.24 9.88 9.88 16.24 7.76"/></svg>
            {:else}
                <svg width="44" height="44" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg>
            {/if}
        </div>

        <h1 class="font-['Lora',serif] text-7xl md:text-8xl font-bold text-[#0D5E56] m-0 mb-4 tracking-tighter">
            {$page.status}
        </h1>

        <h2 class="font-['Lora',serif] text-2xl md:text-3xl text-gray-900 m-0 mb-5">
            {#if $page.status === 404}
                Pagina non trovata
            {:else}
                Ops! Qualcosa è andato storto
            {/if}
        </h2>

        <p class="text-gray-500 text-lg leading-relaxed mb-12 font-light max-w-md mx-auto">
            {#if $page.status === 404}
                La pagina che stai cercando potrebbe essere stata rimossa, aver cambiato nome oppure non è mai esistita.
            {:else}
                {$page.error?.message || "Si è verificato un errore imprevisto durante il caricamento della risorsa."}
            {/if}
        </p>

        <a href="/" class="inline-flex items-center gap-2 bg-[#0D5E56] hover:bg-[#0a4740] text-white font-semibold py-4 px-10 rounded-full transition-all duration-300 shadow-lg hover:shadow-xl hover:-translate-y-1 no-underline">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="19" y1="12" x2="5" y2="12"></line><polyline points="12 19 5 12 12 5"></polyline></svg>
            Torna alla Home
        </a>

    </div>
</div>