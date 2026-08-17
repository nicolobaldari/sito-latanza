<script>
    let sectionEl = $state();
    let visible = $state(false);

    // Gestione del Tab attivo (0 = Marconia, 1 = Ginosa, 2 = Policoro)
    let activeTab = $state(0);

    const sedi = [
        {
            nome: "Marconia",
            città: "Marconia di Pisticci (MT)",
            indirizzo: "Piazza Bologna, 6",
            cap: "75015",
            mappa: "https://maps.google.com/maps?q=Piazza+Bologna,6,75015+Marconia+di+Pisticci+MT&t=&z=16&ie=UTF8&iwloc=&output=embed"
        },
        {
            nome: "Ginosa",
            città: "Ginosa (TA)",
            indirizzo: "Via Armando Diaz, 34",
            cap: "74013",
            mappa: "https://maps.google.com/maps?q=Via+Armando+Diaz,34,74013+Ginosa+TA&t=&z=16&ie=UTF8&iwloc=&output=embed"
        },
        {
            nome: "Policoro",
            città: "Policoro (MT)",
            indirizzo: "Via Giovan Battista Insogna, snc",
            cap: "75025",
            mappa: "https://maps.google.com/maps?q=Via+Giovan+Battista+Insogna,75025+Policoro+MT&t=&z=16&ie=UTF8&iwloc=&output=embed"
        }
    ];

    $effect(() => {
        const observer = new IntersectionObserver(([entry]) => {
            if (entry.isIntersecting) visible = true;
        }, { threshold: 0.1, rootMargin: "0px 0px -50px 0px" });

        if (sectionEl) observer.observe(sectionEl);

        return () => observer.disconnect();
    });
</script>

<section id="contatti" class="py-16 md:py-24 px-5 bg-white relative" bind:this={sectionEl}>
    <div class="max-w-[1200px] mx-auto transition-all duration-1000 ease-out {visible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}">

        <!-- Header Sezione -->
        <div class="text-center max-w-[800px] mx-auto mb-16">
            <h2 class="font-['Lora',serif] text-[2.4rem] md:text-[3rem] text-[#0D5E56] mt-0 mb-4 leading-tight">Contatti & Sedi</h2>
            <p class="text-gray-600 text-lg md:text-[1.15rem] leading-relaxed m-0">Scegli la sede più comoda e prenota la tua valutazione personalizzata. Ricevo su appuntamento.</p>
        </div>

        <div class="flex flex-col lg:flex-row gap-12 xl:gap-16 items-start">
            <!-- Colonna Sinistra: Recapiti Universali -->
            <div class="w-full lg:w-1/3 flex flex-col gap-6">
                <!-- Card Telefono -->
                <a href="tel:+393887596772" class="group bg-gray-50 rounded-2xl p-6 flex items-center gap-5 border border-transparent hover:border-[#0D5E56]/20 hover:bg-white hover:shadow-lg hover:-translate-y-1 transition-all duration-300 no-underline">
                    <div class="w-12 h-12 rounded-full bg-[#0D5E56]/10 text-[#0D5E56] flex items-center justify-center shrink-0 group-hover:bg-[#0D5E56] group-hover:text-white transition-colors">
                        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
                    </div>
                    <div>
                        <p class="text-sm text-gray-500 m-0 mb-1 font-semibold uppercase tracking-wider">Chiama ora</p>
                        <p class="text-xl text-gray-900 font-medium m-0">388 7596772</p>
                    </div>
                </a>

                <!-- Card WhatsApp -->
                <a href="https://wa.me/393887596772" target="_blank" class="group bg-green-50 rounded-2xl p-6 flex items-center gap-5 border border-transparent hover:border-green-200 hover:bg-white hover:shadow-lg hover:shadow-green-100 hover:-translate-y-1 transition-all duration-300 no-underline">
                    <div class="w-12 h-12 rounded-full bg-green-100 text-green-600 flex items-center justify-center shrink-0 group-hover:bg-green-500 group-hover:text-white transition-colors">
                        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z"/></svg>
                    </div>
                    <div>
                        <p class="text-sm text-green-700 m-0 mb-1 font-semibold uppercase tracking-wider">Scrivimi su WhatsApp</p>
                        <p class="text-xl text-gray-900 font-medium m-0">388 7596772</p>
                    </div>
                </a>

                <!-- Card Email -->
                <a href="mailto:f.latanza@hotmail.com" class="group bg-gray-50 rounded-2xl p-6 flex items-center gap-5 border border-transparent hover:border-[#0D5E56]/20 hover:bg-white hover:shadow-lg hover:-translate-y-1 transition-all duration-300 no-underline">
                    <div class="w-12 h-12 rounded-full bg-[#0D5E56]/10 text-[#0D5E56] flex items-center justify-center shrink-0 group-hover:bg-[#0D5E56] group-hover:text-white transition-colors">
                        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
                    </div>
                    <div>
                        <p class="text-sm text-gray-500 m-0 mb-1 font-semibold uppercase tracking-wider">Invia un'email</p>
                        <p class="text-lg text-gray-900 font-medium m-0 truncate max-w-[200px] sm:max-w-none">f.latanza@hotmail.com</p>
                    </div>
                </a>
            </div>

            <!-- Colonna Destra: Sistema a Tab per le Sedi -->
            <div class="w-full lg:w-2/3 bg-white rounded-3xl shadow-xl shadow-[#0D5E56]/5 border border-gray-100 overflow-hidden flex flex-col">

                <!-- Bottoni Tab Sedi -->
                <div class="flex border-b border-gray-200 bg-gray-100/50 flex-wrap sm:flex-nowrap p-1 rounded-t-2xl">
                    {#each sedi as sede, index}
                        <button
                                class="flex-1 py-4 px-2 text-center font-semibold text-[1rem] transition-all duration-300 border-none rounded-t-xl cursor-pointer {activeTab === index ? 'text-[#0D5E56] bg-white shadow-[0_-4px_10px_rgba(0,0,0,0.03)]' : 'bg-transparent text-gray-400 hover:text-gray-600 hover:bg-gray-50'}"
                                onclick={() => activeTab = index}>
                            {sede.nome}
                        </button>
                    {/each}
                </div>

                <!-- Contenuto Dinamico Tab -->
                <div class="p-6 md:p-8 flex-grow flex flex-col">
                    <div class="flex items-start gap-4 mb-6">
                        <div class="w-10 h-10 rounded-full bg-[#0D5E56]/10 text-[#0D5E56] flex items-center justify-center shrink-0 mt-1">
                            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
                        </div>
                        <div>
                            <h3 class="font-['Lora',serif] text-xl md:text-2xl text-gray-900 m-0 mb-1">{sedi[activeTab].città}</h3>
                            <p class="text-gray-600 m-0 text-lg">{sedi[activeTab].indirizzo}, {sedi[activeTab].cap}</p>
                        </div>
                    </div>

                    <!-- Mappa incorporata tramite iFrame di Google Maps -->
                    <div class="w-full rounded-2xl overflow-hidden shadow-inner border border-gray-200 bg-gray-100" style="height: 350px;">
                        <iframe
                                src="{sedi[activeTab].mappa}"
                                width="100%"
                                height="100%"
                                style="border:0;"
                                allowfullscreen=""
                                loading="lazy"
                                referrerpolicy="no-referrer-when-downgrade"
                                title="Mappa Sede {sedi[activeTab].nome}">
                        </iframe>
                    </div>

                    <!-- Link per aprire la posizione nell'app di Google Maps -->
                    <div class="mt-6 text-center">
                        <a href="https://www.google.com/maps/search/?api=1&query={encodeURIComponent(sedi[activeTab].indirizzo + ', ' + sedi[activeTab].città)}" target="_blank" class="inline-flex items-center gap-2 text-[#0D5E56] font-semibold hover:text-[#0a4740] transition-colors no-underline">
                            Apri nell'App di Google Maps
                            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>