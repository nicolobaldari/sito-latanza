<script>
    import Hero from '$lib/components/Hero.svelte';
    import ChiSono from '$lib/components/ChiSono.svelte';
    import Servizi from '$lib/components/Servizi.svelte';
    import Contatti from '$lib/components/Contatti.svelte';
</script>

<svelte:head>
    <link href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400..700;1,400..700&family=Inter:ital,wght@0,100..900;1,100..900&display=swap" rel="stylesheet">

    <!-- SEO di Base -->
    <title>Fisioterapista Osteopata a Marconia, Ginosa, Policoro | DR. Latanza</title>
    <meta name="title" content="Fisioterapista Osteopata a Marconia, Ginosa, Policoro | DR. Latanza" />
    <meta name="description" content="DR. Francesco Latanza, fisioterapista e osteopata. Riabilitazione moderna, tecar, biohacking. Prenota una valutazione a Marconia, Ginosa e Policoro." />
    <meta name="robots" content="index, follow" />
    <link rel="canonical" href="https://www.studiolatanza.it/" />

    <!-- Open Graph (Facebook, LinkedIn, WhatsApp) -->
    <meta property="og:type" content="website" />
    <meta property="og:url" content="https://www.studiolatanza.it/" />
    <meta property="og:title" content="Fisioterapista Osteopata a Marconia, Ginosa, Policoro | DR. Latanza" />
    <meta property="og:description" content="Dr. Francesco Latanza, fisioterapista e osteopata. Riabilitazione moderna, tecar, biohacking. Prenota una valutazione a Marconia, Ginosa e Policoro." />
    <meta property="og:image" content="https://www.studiolatanza.it/studio-latanza-social.png" />
    <meta property="og:locale" content="it_IT" />
    <meta property="og:site_name" content="Dr. Francesco Latanza - Studio di Fisioterapia e Osteopatia" />

    <!-- Twitter Card -->
    <meta property="twitter:card" content="summary_large_image" />
    <meta property="twitter:url" content="https://www.studiolatanza.it/" />
    <meta property="twitter:title" content="Fisioterapista Osteopata a Marconia, Ginosa, Policoro | Dr. Latanza" />
    <meta property="twitter:description" content="Dr. Francesco Latanza, fisioterapista e osteopata. Riabilitazione moderna, tecar, biohacking. Prenota una valutazione a Marconia, Ginosa e Policoro." />
    <meta property="twitter:image" content="https://www.studiolatanza.it/studio-latanza-social.png" />

    <!-- Schema.org JSON-LD (Local SEO Multi-Sede) -->
    <script type="application/ld+json">
        {
            "@context": "https://schema.org",
            "@graph": [
            {
                "@type": "Physician",
                "@id": "https://www.studiolatanza.it/#physician",
                "name": "Dr. Francesco Latanza",
                "description": "Fisioterapista, Osteopata D.O. Specializzato in riabilitazione moderna, fisioterapia, osteopatia, neuroscienze e tecnologie avanzate.",
                "image": "https://www.studiolatanza.it/foto-dottore.jpeg",
                "url": "https://www.studiolatanza.it/",
                "telephone": "+393887596772",
                "email": "f.latanza@hotmail.com",
                "sameAs": [
                    "https://www.facebook.com/drlatanza",
                    "https://www.instagram.com/dr.latanza/"
                ],
                "medicalSpecialty": [
                    "Physiotherapy",
                    "Osteopathic"
                ],
                "hasCredential": [
                    {
                        "@type": "EducationalOccupationalCredential",
                        "credentialCategory": "degree",
                        "recognizedBy": {
                            "@type": "Organization",
                            "name": "Università degli Studi di Bari"
                        },
                        "name": "Laurea in Fisioterapia"
                    },
                    {
                        "@type": "EducationalOccupationalCredential",
                        "credentialCategory": "degree",
                        "recognizedBy": {
                            "@type": "Organization",
                            "name": "Università di Verona"
                        },
                        "name": "Master Universitario in Osteopatia nelle Disfunzioni NeuroMuscolo-Scheletriche"
                    },
                    {
                        "@type": "EducationalOccupationalCredential",
                        "credentialCategory": "certificate",
                        "recognizedBy": {
                            "@type": "Organization",
                            "name": "Escuela de Osteopatía de Madrid (E.O.M.)"
                        },
                        "name": "Titolo di Osteopata D.O."
                    }
                ]
            },
            {
                "@type": "MedicalClinic",
                "@id": "https://www.studiolatanza.it/#clinic-marconia",
                "name": "Studio di Fisioterapia e Osteopatia - Marconia",
                "url": "https://www.studiolatanza.it/#contatti",
                "telephone": "+393887596772",
                "image": "https://www.studiolatanza.it/foto-dottore.jpeg",
                "priceRange": "$$",
                "address": {
                    "@type": "PostalAddress",
                    "streetAddress": "Piazza Bologna, 6",
                    "addressLocality": "Marconia di Pisticci",
                    "addressRegion": "MT",
                    "postalCode": "75015",
                    "addressCountry": "IT"
                },
                "medicalSpecialty": ["Physiotherapy", "Osteopathic"],
                "parentOrganization": { "@id": "https://www.studiolatanza.it/#physician" }
            },
            {
                "@type": "MedicalClinic",
                "@id": "https://www.studiolatanza.it/#clinic-ginosa",
                "name": "Studio di Fisioterapia e Osteopatia - Ginosa",
                "url": "https://www.studiolatanza.it/#contatti",
                "telephone": "+393887596772",
                "image": "https://www.studiolatanza.it/foto-dottore.jpeg",
                "priceRange": "$$",
                "address": {
                    "@type": "PostalAddress",
                    "streetAddress": "Via Armando Diaz, 34",
                    "addressLocality": "Ginosa",
                    "addressRegion": "TA",
                    "postalCode": "74013",
                    "addressCountry": "IT"
                },
                "medicalSpecialty": ["Physiotherapy", "Osteopathic"],
                "parentOrganization": { "@id": "https://www.studiolatanza.it/#physician" }
            },
            {
                "@type": "MedicalClinic",
                "@id": "https://www.studiolatanza.it/#clinic-policoro",
                "name": "Studio di Fisioterapia e Osteopatia - Policoro",
                "url": "https://www.studiolatanza.it/#contatti",
                "telephone": "+393887596772",
                "image": "https://www.studiolatanza.it/foto-dottore.jpeg",
                "priceRange": "$$",
                "address": {
                    "@type": "PostalAddress",
                    "streetAddress": "Via Giovan Battista Insogna, snc",
                    "addressLocality": "Policoro",
                    "addressRegion": "MT",
                    "postalCode": "75025",
                    "addressCountry": "IT"
                },
                "medicalSpecialty": ["Physiotherapy", "Osteopathic"],
                "parentOrganization": { "@id": "https://www.studiolatanza.it/#physician" }
            }
        ]
        }
    </script>
</svelte:head>

<Hero />
<div class="relative z-20 bg-white shadow-[0_-15px_30px_rgba(0,0,0,0.15)]">
    <ChiSono />
    <Servizi />
    <Contatti />
</div>