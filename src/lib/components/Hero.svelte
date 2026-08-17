<script>
    import { onMount } from 'svelte';
    let loaded = $state(false);
    onMount(() => loaded = true);
</script>

<section class="relative w-full h-screen min-h-[600px] flex items-center bg-[#0D5E56] overflow-hidden sticky top-0 -z-10 box-border">

    <!-- Livello 1: Immagine -->
    <!-- Opacità maggiore su mobile per garantire una buona visibilità della foto -->
    <div class="absolute inset-0 md:left-auto md:right-0 md:w-[65vw] h-full z-0 transition-opacity duration-[1.5s] delay-200 {loaded ? 'opacity-70 md:opacity-100' : 'opacity-0'}">
        <img
                src="/foto-dottore.jpeg"
                alt="Dr. Francesco Latanza esegue un trattamento osteopatico"
                class="w-full h-full object-cover object-[60%_center] md:object-[center_right]"
        />
    </div>

    <!-- Livello 2: Overlay Gradiente -->
    <!-- Gradiente più leggero su mobile per non coprire eccessivamente la foto -->
    <div class="absolute inset-0 pointer-events-none z-[1]
        bg-[linear-gradient(to_top,#0D5E56_0%,rgba(13,94,86,0.2)_100%)]
        md:bg-[linear-gradient(to_right,#0D5E56_0%,#0D5E56_35%,rgba(13,94,86,0.7)_50%,rgba(13,94,86,0.3)_65%,transparent_85%)]">
    </div>

    <!-- Livello 3: Container Principale per i testi -->
    <div class="relative z-10 flex flex-col md:flex-row items-center w-full max-w-[1440px] mx-auto h-full pointer-events-none">

        <!-- Colonna Testo -->
        <div class="w-full md:w-1/2 px-5 md:pl-[8%] text-center md:text-left text-white mt-[20%] md:mt-0 transition-all duration-[1.2s] ease-out delay-500 pointer-events-auto {loaded ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}">
            <h1 class="font-['Lora',serif] text-[2.5rem] md:text-5xl lg:text-[4rem] font-normal mb-4 leading-tight drop-shadow-xl">
                Dr. Francesco Latanza
            </h1>
            <p class="font-['Inter',sans-serif] text-xl md:text-[1.5rem] font-light opacity-90 tracking-wide drop-shadow-md">
                Studi di Osteopatia e Fisioterapia
            </p>
        </div>

    </div>
</section>