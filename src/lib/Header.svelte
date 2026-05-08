<script>
    import Navigation from './Navigation.svelte';
</script>


<header class="header">
    <Navigation />
</header>


<style>
    .header {
        padding: 1px var(--space-xl) 1px;
        border-bottom: 1px solid var(--color-line);
    }

    @keyframes fadeInTitle {
        from {
            opacity: 0;
            transform: translateY(10px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    @media (max-width: 760px) {
        .header {
            grid-template-columns: 1fr auto;
            padding: 18px 18px 10px;
        }
    }
</style>
