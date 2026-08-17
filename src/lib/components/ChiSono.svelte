<script>
    let visible = $state(false);
    let sectionEl = $state();

    $effect(() => {
        const observer = new IntersectionObserver(([entry]) => {
            if (entry.isIntersecting) visible = true;
        }, { threshold: 0.1, rootMargin: "0px 0px -50px 0px" });

        if (sectionEl) observer.observe(sectionEl);

        return () => observer.disconnect();
    });
</script>

<section id="chi-siamo" class="py-16 md:py-24 px-5" bind:this={sectionEl}>
    <div class="max-w-[1200px] mx-auto">

        <!-- Intestazione Centrale: Titolo e Citazione (Full Width) -->
        <div class="text-center max-w-[800px] mx-auto mb-16 transition-all duration-1000 ease-out {visible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-5'}">
            <h2 class="text-[#0D5E56] text-[2.4rem] md:text-[3rem] leading-tight mt-0 mb-6 font-['Lora',serif]">
                Chi Sono
            </h2>
            <p class="text-[#0D5E56] text-xl md:text-2xl font-['Lora',serif] font-medium italic">
                "Ogni sintomo racconta una storia che va oltre il punto in cui si manifesta."
            </p>
        </div>

        <!-- Layout Editoriale a 2 Colonne (50% / 50%) -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-12 xl:gap-16 items-start transition-all duration-1000 delay-200 ease-out {visible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}">

            <!-- Colonna Sinistra: Approccio Clinico -->
            <div class="text-gray-700 text-lg leading-relaxed text-left">
                <h3 class="font-['Lora',serif] text-2xl text-gray-900 mb-6 border-b-2 border-[#0D5E56]/30 inline-block pb-2">
                    Il mio approccio clinico
                </h3>
                <p class="mb-5">
                    Il corpo non è la semplice somma di articolazioni e muscoli, ma un <strong class="text-gray-900">sistema biologico complesso</strong> in cui movimento, sistema nervoso, immunitario e stile di vita dialogano costantemente. Per questo, ogni mio percorso terapeutico inizia con una valutazione profonda per comprendere l'origine del disturbo, non solo il sintomo.
                </p>
                <p>
                    Credo in una <strong class="text-gray-900">riabilitazione moderna</strong>. Nella mia pratica clinica integro fisioterapia, osteopatia e neuroscienze con tecnologie avanzate (come ecografia muscolo-scheletrica, biohacking e neuro-modulazione) per offrire percorsi <strong class="text-gray-900">altamente personalizzati</strong> e basati sulle più recenti evidenze scientifiche.
                </p>
            </div>

            <!-- Colonna Destra: Formazione -->
            <div class="text-gray-700 text-lg leading-relaxed text-left">
                <h3 class="font-['Lora',serif] text-2xl text-gray-900 mb-6 border-b-2 border-[#0D5E56]/30 inline-block pb-2">
                    Formazione e Specializzazioni
                </h3>
                <ul class="space-y-5 m-0 p-0 list-none">
                    <li class="flex items-start gap-4">
                        <svg class="w-6 h-6 text-[#0D5E56] shrink-0 mt-1" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                        <span><strong class="text-gray-900">Laurea in Fisioterapia</strong> presso l'Università degli Studi di Bari.</span>
                    </li>
                    <li class="flex items-start gap-4">
                        <svg class="w-6 h-6 text-[#0D5E56] shrink-0 mt-1" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                        <span><strong class="text-gray-900">Master Universitario in Osteopatia</strong> nelle Disfunzioni NeuroMuscolo-Scheletriche (Università di Verona).</span>
                    </li>
                    <li class="flex items-start gap-4">
                        <svg class="w-6 h-6 text-[#0D5E56] shrink-0 mt-1" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                        <span><strong class="text-gray-900">Titolo di Osteopata D.O.</strong> presso la Escuela de Osteopatía de Madrid (E.O.M.).</span>
                    </li>
                    <li class="flex items-start gap-4">
                        <svg class="w-6 h-6 text-[#0D5E56] shrink-0 mt-1" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                        <span>Perfezionamento in <strong class="text-gray-900">Psico-neuro-immunologia Clinica (PNEI)</strong> presso l'Università Pontificia di Salamanca.</span>
                    </li>
                </ul>
            </div>

        </div>

        <!-- Chiusura Full-Width: La Mia Missione -->
        <div class="mt-16 md:mt-20 transition-all duration-1000 delay-400 ease-out {visible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}">
            <div class="p-8 md:p-12 bg-[#0D5E56]/5 border-t-4 border-[#0D5E56] rounded-2xl shadow-sm max-w-[900px] mx-auto text-center">
                <p class="text-sm font-bold text-[#0D5E56] uppercase tracking-widest mb-4">La mia Missione</p>
                <p class="text-[#0f3d35] font-['Lora',serif] text-xl md:text-2xl font-medium m-0 leading-relaxed italic">
                    "Per me la riabilitazione non significa semplicemente trattare un dolore, ma aiutare ogni persona a comprendere il proprio corpo, recuperarne la funzione e migliorare la qualità di vita riconoscendo le proprie potenzialità."
                </p>
            </div>
        </div>

    </div>
</section>
