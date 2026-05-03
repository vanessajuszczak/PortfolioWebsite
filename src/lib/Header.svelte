<script>
    import { asset, resolve } from '$app/paths';
    import Navigation from './Navigation.svelte';
</script>


<header class="header">
    <a href={resolve('/')} class="logo-area">
        <img src={asset("/logo.png")} alt="Site Logo" />
    </a>
    <Navigation />
</header>


<style>
    .header {
        display: grid;
        grid-template-columns: 180px 1fr;
        align-items: center;
        gap: var(--space-md);
        padding: 1px var(--space-xl) 1px;
        border-bottom: 1px solid var(--color-line);
    }

    .logo-area {
        display: inline-flex;
        align-items: center;
        width: 110px;
    }

    .logo-area img {
        width: 100%;
        height: auto;
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

        .logo-area {
            width: 92px;
        }
    }
</style>
