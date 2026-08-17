<script>
    import { slide } from 'svelte/transition';

    let sectionEl = $state();
    let visible = $state(false);

    let isModalOpen = $state(false);
    let selectedService = $state(null);
    let activeAccordion = $state(null);

    function openModal(servizio) {
        selectedService = servizio;
        isModalOpen = true;
        if (typeof window !== 'undefined') document.body.style.overflow = 'hidden';
    }

    function closeModal() {
        isModalOpen = false;
        setTimeout(() => selectedService = null, 300);
        if (typeof window !== 'undefined') document.body.style.overflow = '';
    }

    function toggleAccordion(id) {
        activeAccordion = activeAccordion === id ? null : id;
    }

    const serviziPrincipali = [
        {
            id: 'sp1',
            titolo: "Osteopatia",
            descBreve: "Un approccio terapeutico manuale che analizza le relazioni funzionali tra sistema muscolo-scheletrico, tessuto fasciale, sistema nervoso e componente viscerale.",
            ctaText: "Scopri il trattamento",
            descLunga: `
                <p class='mb-6'>L'osteopatia è un approccio terapeutico manuale che, attraverso una valutazione globale del paziente, analizza le relazioni funzionali tra <strong>sistema muscolo-scheletrico, tessuto fasciale, sistema nervoso e componente viscerale</strong>.</p>
                <div class='bg-[#0D5E56]/5 rounded-2xl p-5 md:p-6 border-l-4 border-[#0D5E56] relative overflow-hidden'>
                    <h4 class='font-["Lora",serif] text-lg font-semibold text-[#0D5E56] m-0 mb-3'>Il Trattamento</h4>
                    <p class='m-0 text-gray-700 leading-relaxed text-[1.05rem]'>Il trattamento si basa su tecniche manuali mirate a migliorare la mobilità dei tessuti, modulare il dolore e favorire un'adeguata integrazione neuro-muscoloscheletrica.</p>
                </div>`
        },
        {
            id: 'sp2',
            titolo: "Fisioterapia",
            descBreve: "Il pilastro del recupero funzionale: mira a ridurre il dolore, ripristinare il movimento, migliorare la funzione e prevenire le recidive.",
            ctaText: "Scopri il trattamento",
            descLunga: `
                <p class='mb-6'>È il <strong>pilastro del recupero funzionale</strong> e della riabilitazione: mira a ridurre il dolore, ripristinare il movimento, migliorare la funzione e prevenire le recidive.</p>
                <div class='bg-[#0D5E56]/5 rounded-2xl p-5 md:p-6 border-l-4 border-[#0D5E56] relative overflow-hidden'>
                    <h4 class='font-["Lora",serif] text-lg font-semibold text-[#0D5E56] m-0 mb-3'>Approccio Integrato</h4>
                    <p class='m-0 text-gray-700 leading-relaxed text-[1.05rem]'>Attraverso una valutazione clinica approfondita, integra esercizio terapeutico, terapia manuale, tecnologie riabilitative e l'approccio osteopatico.</p>
                </div>`
        },
        {
            id: 'sp3',
            titolo: "Terapie Eco-guidate",
            descBreve: "Visualizzazione ecografica dinamica in tempo reale per guidare con precisione millimetrica il trattamento verso il tessuto coinvolto.",
            ctaText: "Scopri l'innovazione",
            descLunga: `
                <p class='mb-6'>Le terapie eco-guidate rappresentano uno degli strumenti più avanzati della medicina riabilitativa moderna. Grazie alla <strong>visualizzazione ecografica dinamica</strong>, è possibile guidare con precisione il trattamento.</p>
                <div class='bg-[#0D5E56]/5 rounded-2xl p-5 md:p-6 border-l-4 border-[#0D5E56] relative overflow-hidden'>
                    <h4 class='font-["Lora",serif] text-lg font-semibold text-[#0D5E56] m-0 mb-3'>Obiettivo Terapeutico</h4>
                    <p class='m-0 text-gray-700 leading-relaxed text-[1.05rem]'>L'integrazione tra ecografia, valutazione clinica e competenze riabilitative consente di realizzare interventi mirati, sicuri e altamente personalizzati.</p>
                </div>`
        },
        {
            id: 'sp4',
            titolo: "Biohacking & Nano-tech",
            descBreve: "Integra neuroscienze, PNEI e l'innovazione indossabile Taopatch® per ottimizzare il controllo posturale e il benessere psicofisico.",
            ctaText: "Esplora le tecniche",
            descLunga: `
                <p class='mb-6'>Il biohacking rappresenta un approccio innovativo che integra <strong>neuroscienze, Psico-neuroimmunologia Clinica e dispositivi medici brevettati come Taopatch®</strong>.</p>
                <div class='bg-[#0D5E56]/5 rounded-2xl p-5 md:p-6 border-l-4 border-[#0D5E56] relative overflow-hidden'>
                    <h4 class='font-["Lora",serif] text-lg font-semibold text-[#0D5E56] m-0 mb-3'>L'Ottimizzazione</h4>
                    <p class='m-0 text-gray-700 leading-relaxed text-[1.05rem]'>Attraverso la modulazione dei processi neurofisiologici, è possibile migliorare il controllo motorio, la capacità di recupero e la qualità del movimento.</p>
                </div>`
        }
    ];

    const terapieStrumentali = [
        {
            id: 'ts1',
            titolo: "Tecarterapia",
            descBreve: "Radiofrequenze avanzate per stimolare i processi di riparazione, aumentare la microcircolazione e ridurre l'infiammazione.",
            ctaText: "Scopri la terapia",
            descLunga: `
                <p class='mb-6'>La Tecarterapia è una tecnologia avanzata che utilizza radiofrequenze per stimolare i <strong>naturali processi di riparazione e rigenerazione dei tessuti</strong>.</p>
                <div class='bg-[#0D5E56]/5 rounded-2xl p-5 md:p-6 border-l-4 border-[#0D5E56] relative overflow-hidden'>
                    <h4 class='font-["Lora",serif] text-lg font-semibold text-[#0D5E56] m-0 mb-3'>Azione Terapeutica</h4>
                    <p class='m-0 text-gray-700 leading-relaxed text-[1.05rem]'>Favorisce l'aumento della microcircolazione, migliora il metabolismo cellulare e contribuisce alla riduzione del dolore.</p>
                </div>`
        },
        {
            id: 'ts2',
            titolo: "Onde d'Urto",
            descBreve: "Impulsi meccanici ad alta energia per stimolare la riparazione tissutale in tendinopatie, calcificazioni e fasciti plantari.",
            ctaText: "Scopri la terapia",
            descLunga: `
                <p class='mb-6'>Le Onde d'Urto Focali e Radiali rappresentano una delle terapie più efficaci per il trattamento delle <strong>patologie muscolo-scheletriche croniche</strong>.</p>
                <div class='bg-[#0D5E56]/5 rounded-2xl p-5 md:p-6 border-l-4 border-[#0D5E56] relative overflow-hidden'>
                    <h4 class='font-["Lora",serif] text-lg font-semibold text-[#0D5E56] m-0 mb-3'>Meccanismo d'Azione</h4>
                    <p class='m-0 text-gray-700 leading-relaxed text-[1.05rem]'>Attraverso impulsi meccanici ad alta energia stimolano i processi biologici di riparazione tissutale e modulano il dolore.</p>
                </div>`
        },
        {
            id: 'ts3',
            titolo: "Laserterapia",
            descBreve: "Luce ad elevata intensità per raggiungere i tessuti profondi, esercitando un'azione antalgica, antinfiammatoria e biostimolante.",
            ctaText: "Scopri la terapia",
            descLunga: `
                <p class='mb-6'>La Laserterapia ad Alta Potenza sfrutta una luce ad elevata intensità capace di raggiungere i tessuti profondi, esercitando un'azione <strong>antalgica, antinfiammatoria e biostimolante</strong>.</p>
                <div class='bg-[#0D5E56]/5 rounded-2xl p-5 md:p-6 border-l-4 border-[#0D5E56] relative overflow-hidden'>
                    <h4 class='font-["Lora",serif] text-lg font-semibold text-[#0D5E56] m-0 mb-3'>Recupero Rapido</h4>
                    <p class='m-0 text-gray-700 leading-relaxed text-[1.05rem]'>Grazie alla sua elevata precisione, favorisce i processi di recupero biologico e accelera il recupero funzionale.</p>
                </div>`
        },
        {
            id: 'ts4',
            titolo: "Ossigeno-terapia",
            descBreve: "Approccio innovativo per modulare lo stress ossidativo, ottimizzare il metabolismo cellulare e supportare il recupero sistemico.",
            ctaText: "Scopri l'innovazione",
            descLunga: `
                <p class='mb-6'>L'ossigeno è indispensabile per il metabolismo cellulare. Associato all'idrogeno molecolare, dà origine a un approccio innovativo orientato al benessere e al supporto del recupero.</p>
                <div class='bg-[#0D5E56]/5 rounded-2xl p-5 md:p-6 border-l-4 border-[#0D5E56] relative overflow-hidden'>
                    <h4 class='font-["Lora",serif] text-lg font-semibold text-[#0D5E56] m-0 mb-3'>Integrazione Clinica</h4>
                    <p class='m-0 text-gray-700 leading-relaxed text-[1.05rem]'>Supporta i fisiologici processi di adattamento dell'organismo, contribuendo alla modulazione dello stress ossidativo.</p>
                </div>`
        }
    ];

    $effect(() => {
        const observer = new IntersectionObserver(([entry]) => {
            if (entry.isIntersecting) visible = true;
        }, { threshold: 0.05, rootMargin: "0px 0px -50px 0px" });
        if (sectionEl) observer.observe(sectionEl);
        return () => observer.disconnect();
    });
</script>

<section id="servizi" class="bg-white py-16 md:py-24 px-5 relative" bind:this={sectionEl}>
    <div class="max-w-[1200px] mx-auto transition-all duration-1000 ease-out {visible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'}">

        <div class="flex flex-col lg:flex-row items-center gap-12 lg:gap-20 mb-20 md:mb-32">
            <div class="w-full lg:w-1/2 flex flex-col justify-center text-left">
                <h2 class="font-['Lora',serif] text-[2.8rem] md:text-6xl lg:text-7xl text-[#0D5E56] mt-0 mb-6 leading-tight">
                    I Nostri Servizi
                </h2>
                <p class="text-gray-500 text-lg md:text-xl font-light leading-relaxed m-0 max-w-xl">
                    Percorsi terapeutici altamente personalizzati, fondati sul ragionamento clinico e sulle più attuali evidenze scientifiche per risolvere il problema alla radice.
                </p>
            </div>
            <div class="w-full lg:w-1/2 relative">
                <div class="aspect-[4/3] lg:aspect-square rounded-[2.5rem] overflow-hidden shadow-2xl shadow-[#0D5E56]/10">
                    <img
                            src="/studio-latanza-social.png"
                            alt="Trattamenti professionali e cura del paziente"
                            class="w-full h-full object-cover object-[center_20%]"
                    />
                </div>
            </div>
        </div>

        <div class="mb-20 md:mb-32">
            <p class="text-[#0D5E56] font-semibold tracking-[0.2em] uppercase text-sm md:text-base mb-6 md:mb-8 ml-2">01. Approccio Clinico</p>

            <div class="hidden md:block border-t border-gray-200">
                {#each serviziPrincipali as s}
                    <!-- Elemento reso interattivo con <button> per l'accessibilità da tastiera -->
                    <button class="w-full text-left bg-transparent border-none p-0 m-0 group flex border-b border-gray-200 transition-colors duration-400 hover:bg-gray-50/70 cursor-pointer" onclick={() => openModal(s)}>
                        <div class="w-1/3 py-12 pl-6 pr-4 flex items-center">
                            <h3 class="font-['Lora',serif] text-3xl font-bold text-gray-900 group-hover:text-[#0D5E56] transition-colors duration-300">{s.titolo}</h3>
                        </div>
                        <div class="w-2/3 py-12 pr-8 flex flex-col justify-center">
                            <p class="text-gray-500 text-[1.1rem] leading-relaxed mb-4 max-w-2xl">{s.descBreve}</p>
                            <span class="inline-flex items-center gap-2 text-[#0D5E56] font-semibold text-[1rem]">
                                {s.ctaText}
                                <span class="transition-transform duration-300 group-hover:translate-x-2">
                                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
                                </span>
                            </span>
                        </div>
                    </button>
                {/each}
            </div>

            <div class="md:hidden border-t border-gray-200">
                {#each serviziPrincipali as s}
                    <div class="border-b border-gray-200 overflow-hidden">
                        <button class="w-full py-6 px-2 flex justify-between items-center text-left bg-transparent border-none cursor-pointer" onclick={() => toggleAccordion(s.id)}>
                            <span class="font-['Lora',serif] text-[1.4rem] font-bold {activeAccordion === s.id ? 'text-[#0D5E56]' : 'text-gray-900'} transition-colors">{s.titolo}</span>
                            <div class="w-8 h-8 rounded-full border border-gray-200 flex items-center justify-center shrink-0 transition-transform duration-300 {activeAccordion === s.id ? 'rotate-180 bg-[#0D5E56]/5 border-[#0D5E56]/30 text-[#0D5E56]' : 'text-gray-400'}">
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="6 9 12 15 18 9"></polyline></svg>
                            </div>
                        </button>
                        {#if activeAccordion === s.id}
                            <div transition:slide={{ duration: 300, axis: 'y' }} class="px-2 pb-8">
                                <p class="text-gray-500 text-[1.05rem] leading-relaxed m-0 mb-5">{s.descBreve}</p>
                                <button onclick={() => openModal(s)} class="inline-flex items-center gap-2 text-[#0D5E56] font-semibold text-[1rem] bg-transparent border-none p-0 cursor-pointer">
                                    {s.ctaText} &rarr;
                                </button>
                            </div>
                        {/if}
                    </div>
                {/each}
            </div>
        </div>

        <div>
            <p class="text-[#0D5E56] font-semibold tracking-[0.2em] uppercase text-sm md:text-base mb-6 md:mb-8 ml-2">02. Terapie Strumentali</p>

            <div class="hidden md:block border-t border-gray-200">
                {#each terapieStrumentali as ts}
                    <button class="w-full text-left bg-transparent border-none p-0 m-0 group flex border-b border-gray-200 transition-colors duration-400 hover:bg-gray-50/70 cursor-pointer" onclick={() => openModal(ts)}>
                        <div class="w-1/3 py-12 pl-6 pr-4 flex items-center">
                            <h3 class="font-['Lora',serif] text-3xl font-bold text-gray-900 group-hover:text-[#0D5E56] transition-colors duration-300">{ts.titolo}</h3>
                        </div>
                        <div class="w-2/3 py-12 pr-8 flex flex-col justify-center">
                            <p class="text-gray-500 text-[1.1rem] leading-relaxed mb-4 max-w-2xl">{ts.descBreve}</p>
                            <span class="inline-flex items-center gap-2 text-[#0D5E56] font-semibold text-[1rem]">
                                {ts.ctaText}
                                <span class="transition-transform duration-300 group-hover:translate-x-2">
                                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
                                </span>
                            </span>
                        </div>
                    </button>
                {/each}
            </div>

            <div class="md:hidden border-t border-gray-200">
                {#each terapieStrumentali as ts}
                    <div class="border-b border-gray-200 overflow-hidden">
                        <button class="w-full py-6 px-2 flex justify-between items-center text-left bg-transparent border-none cursor-pointer" onclick={() => toggleAccordion(ts.id)}>
                            <span class="font-['Lora',serif] text-[1.4rem] font-bold {activeAccordion === ts.id ? 'text-[#0D5E56]' : 'text-gray-900'} transition-colors">{ts.titolo}</span>
                            <div class="w-8 h-8 rounded-full border border-gray-200 flex items-center justify-center shrink-0 transition-transform duration-300 {activeAccordion === ts.id ? 'rotate-180 bg-[#0D5E56]/5 border-[#0D5E56]/30 text-[#0D5E56]' : 'text-gray-400'}">
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="6 9 12 15 18 9"></polyline></svg>
                            </div>
                        </button>
                        {#if activeAccordion === ts.id}
                            <div transition:slide={{ duration: 300, axis: 'y' }} class="px-2 pb-8">
                                <p class="text-gray-500 text-[1.05rem] leading-relaxed m-0 mb-5">{ts.descBreve}</p>
                                <button onclick={() => openModal(ts)} class="inline-flex items-center gap-2 text-[#0D5E56] font-semibold text-[1rem] bg-transparent border-none p-0 cursor-pointer">
                                    {ts.ctaText} &rarr;
                                </button>
                            </div>
                        {/if}
                    </div>
                {/each}
            </div>
        </div>
    </div>

    {#if isModalOpen && selectedService}
        <!-- svelte-ignore a11y_click_events_have_key_events -->
        <!-- svelte-ignore a11y_no_static_element_interactions -->
        <div class="fixed inset-0 z-[1000] flex items-center justify-center p-4 bg-[#082923]/70 backdrop-blur-sm transition-opacity duration-300" onclick={closeModal}>
            <!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
            <div role="dialog" aria-modal="true" class="bg-white w-full max-w-2xl rounded-3xl shadow-2xl overflow-hidden relative transform transition-all duration-300 scale-100 opacity-100 max-h-[90vh] flex flex-col" onclick={(e) => e.stopPropagation()}>
                <div class="p-5 md:p-8 pb-5 flex justify-between items-center border-b border-gray-100 relative shrink-0">
                    <h3 class="font-['Lora',serif] text-2xl md:text-3xl text-[#0D5E56] m-0 leading-tight">{selectedService.titolo}</h3>
                    <button onclick={closeModal} aria-label="Chiudi finestra" class="bg-gray-100 hover:bg-gray-200 text-gray-500 rounded-full w-8 h-8 flex items-center justify-center border-none cursor-pointer transition-colors shrink-0 ml-4">
                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
                    </button>
                </div>
                <div class="px-5 md:px-8 pt-6 pb-10 overflow-y-auto text-gray-700 text-[1rem] md:text-[1.05rem] leading-relaxed">
                    {@html selectedService.descLunga}
                </div>
            </div>
        </div>
    {/if}
</section>