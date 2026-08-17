<script>
    import './layout.css';
    import Navbar from '$lib/components/Navbar.svelte';
    import Footer from '$lib/components/Footer.svelte';

    let { children } = $props();
</script>

<!-- Contenitore flex ad altezza minima pari allo schermo -->
<div class="flex flex-col min-h-screen">
    <Navbar />
    <!-- flex-grow espande <main> per occupare lo spazio disponibile, mantenendo il footer in fondo alla pagina -->
    <main class="flex-grow flex flex-col">
        {@render children()}
    </main>
    <Footer />
</div>