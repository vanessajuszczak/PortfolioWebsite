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
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 var(--space-lg);
        background-color: var(--color-secondary);
        box-shadow: var(--shadow-md);
        border-bottom: 1px solid var(--color-border);
        position: relative;
        z-index: 100;
    }

    .logo-area {
        display: flex;
        align-items: center;
        gap: var(--space-sm);
        font-family: var(--font-heading);
    }

    .logo-area img {
        width: 96px;
        height: auto;
        border-radius: 0;
        box-shadow: none;
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

    @media (max-width: 1024px) {
        .header {
            flex-direction: row;
            justify-content: space-between;
            align-items: center;
            padding: var(--space-sm) var(--space-md);
        }

        .logo-area {
            justify-content: flex-start;
            width: auto;
        }

        .logo-area img {
            width: 72px;
            height: auto;
        }
    }
</style>
