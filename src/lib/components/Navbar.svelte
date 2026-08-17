<script>
    import { slide } from 'svelte/transition';

    let y = $state(0);
    // La navbar compare se scorriamo o se il menu è aperto
    let showNavbar = $derived(y > 150 || isMenuOpen);

    let isMenuOpen = $state(false);

    function toggleMenu() {
        isMenuOpen = !isMenuOpen;
    }

    function closeMenu() {
        isMenuOpen = false;
    }
</script>

<svelte:window bind:scrollY={y} />

<nav class="fixed top-0 left-0 w-full z-[1000] transition-all duration-500 ease-in-out {showNavbar ? 'opacity-100 visible translate-y-0 bg-white/95 backdrop-blur-md shadow-sm' : 'opacity-0 invisible -translate-y-4'}">

    <!-- Contenitore Principale -->
    <div class="max-w-[1200px] mx-auto px-5 md:px-8 h-[70px] flex justify-between items-center relative z-20 bg-transparent">

        <!-- Logo -->
        <a href="/" class="block z-50 transform md:-translate-y-1" onclick={closeMenu}>
            <!-- Altezza contenuta per un migliore bilanciamento visivo del logo -->
            <img src="/Logo_Latanza_senza_sfondo.png" alt="Logo Dr. Latanza" class="h-[40px] md:h-[50px] w-auto block" />
        </a>

        <!-- Menu Desktop -->
        <ul class="hidden md:flex gap-8 m-0 p-0 list-none">
            <li><a href="#chi-siamo" class="no-underline text-gray-700 font-medium text-[1.05rem] transition-colors hover:text-[#0D5E56]">Chi Sono</a></li>
            <li><a href="#servizi" class="no-underline text-gray-700 font-medium text-[1.05rem] transition-colors hover:text-[#0D5E56]">Servizi</a></li>
            <li><a href="#contatti" class="no-underline text-gray-700 font-medium text-[1.05rem] transition-colors hover:text-[#0D5E56]">Contatti</a></li>
        </ul>

        <!-- Tasto Hamburger -->
        <button
                class="md:hidden flex flex-col justify-center items-center w-10 h-10 border-none bg-transparent cursor-pointer z-50"
                onclick={toggleMenu}
                aria-label="Menu"
        >
            <span class="bg-[#0D5E56] block transition-all duration-300 ease-out h-[2px] w-6 rounded-sm {isMenuOpen ? 'rotate-45 translate-y-[6px]' : '-translate-y-1'}"></span>
            <span class="bg-[#0D5E56] block transition-all duration-300 ease-out h-[2px] w-6 rounded-sm my-0.5 {isMenuOpen ? 'opacity-0' : 'opacity-100'}"></span>
            <span class="bg-[#0D5E56] block transition-all duration-300 ease-out h-[2px] w-6 rounded-sm {isMenuOpen ? '-rotate-45 -translate-y-[6px]' : 'translate-y-1'}"></span>
        </button>

    </div>

    <!-- Dropdown Menu Mobile Semplificato -->
    {#if isMenuOpen}
        <div
                class="md:hidden absolute top-[70px] left-0 w-full bg-white shadow-lg border-t border-gray-100 z-10"
                transition:slide={{ duration: 300, axis: 'y' }}
        >
            <ul class="flex flex-col m-0 p-4 px-5 list-none">
                <li>
                    <a href="#chi-siamo" onclick={closeMenu} class="block py-3 no-underline text-gray-700 font-medium text-[1.1rem] border-b border-gray-50">
                        Chi Sono
                    </a>
                </li>
                <li>
                    <a href="#servizi" onclick={closeMenu} class="block py-3 no-underline text-gray-700 font-medium text-[1.1rem] border-b border-gray-50">
                        Servizi
                    </a>
                </li>
                <li>
                    <a href="#contatti" onclick={closeMenu} class="block py-3 no-underline text-gray-700 font-medium text-[1.1rem]">
                        Contatti
                    </a>
                </li>
            </ul>
        </div>
    {/if}
</nav>