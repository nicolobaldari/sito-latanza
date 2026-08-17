<script>
    import './layout.css';
    import Navbar from '$lib/components/Navbar.svelte';
    import Footer from '$lib/components/Footer.svelte';

    // In Svelte 5 si importano così i contenuti figli
    let { children } = $props();
</script>

<!-- Contenitore flex che occupa sempre ALMENO tutto lo schermo (min-h-screen) -->
<div class="flex flex-col min-h-screen">
    <Navbar />
    <!-- flex-grow ordina a <main> di espandersi per occupare tutto lo spazio vuoto, spingendo giù il footer -->
    <main class="flex-grow flex flex-col">
        {@render children()}
    </main>
    <Footer />
</div>