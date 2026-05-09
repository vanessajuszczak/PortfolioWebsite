<script>
    // Import components
    import Header from "$lib/Header.svelte";
    import Footer from "$lib/Footer.svelte";
    import {page} from "$app/state";
</script>

<svelte:head>
    <title>Vanessa</title>
</svelte:head>


<div id="layout-container">
    <!-- Header -->
    <Header />

    <!-- Page Content -->
    <main id="main-content" tabindex="-1">
        {#key page.url.pathname}
            <div class="page-transition">
                <slot />
            </div>
        {/key}
    </main>

    <!-- Footer -->
    <Footer />
</div>



<style>
    #layout-container {
        display: flex;
        flex-direction: column;
        min-height: 100vh;
        color: var(--text-primary);
        font-family: var(--font-body);
    }

    main {
        flex: 1;
        width: 100%;
        display: flex;
        flex-direction: column;
        position: relative;
        isolation: isolate;
    }

    main::before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        min-height: 100%;
        width: 100%;
        opacity: 0.66;
        z-index: -1;
    }

    .page-transition {
        width: 100%;
        animation: pageLoad 0.6s ease;
    }

    @keyframes pageLoad {
        from {
            opacity: 0;
            transform: translateY(18px);
        }

        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    @media (max-width: 768px) {
        main {
            padding: 0;
        }
    }
</style>
