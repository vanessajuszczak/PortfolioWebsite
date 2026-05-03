<script>
    import { page } from '$app/state';
    import {resolve} from '$app/paths';
    

    const navigationItems = [
        { name: 'About', path: '/about/' },
        { name: 'Projects', path: '/projects/' },
        { name: 'CV', path: '/cv/' },
        { name: 'Contact', path: '/contact/' }
    ];

    let isOpen = false;

    function hideMenu() {
        isOpen = false;
    }
</script>


<nav class="nav" aria-label="Main navigation">
    <button
        class="burger"
        on:click={() => (isOpen = !isOpen)}
        aria-label="Toggle navigation menu"
        aria-expanded={isOpen}
        aria-controls="main-menu"
    >
        ☰
    </button>

    <ul id="main-menu" class:open={isOpen}>
        {#each navigationItems as item}
            <li class="nav-item">
                <a 
                    href={resolve(item.path)}
                    class:active={page.url.pathname === resolve(item.path)}
                    on:click={hideMenu}
                >{item.name}</a>
            </li>
        {/each}
    </ul>
</nav>


<style>
    .nav {
        justify-self: stretch;
    }

    .nav ul {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: var(--space-md);
        list-style: none;
        margin: 0;
        padding: 0;
    }

    .nav-item {
        animation: fadeUp 0.4s ease forwards;
    }

    .nav-item:nth-child(1) { animation-delay: 0.2s; }
    .nav-item:nth-child(2) { animation-delay: 0.4s; }
    .nav-item:nth-child(3) { animation-delay: 0.6s; }
    .nav-item:nth-child(4) { animation-delay: 0.8s; }

    .nav a {
        display: inline-flex;
        min-height: 10px;
        align-items: center;
        font-size: var(--font-base);
        font-weight: 700;
        color: var(--text-primary);
        text-transform: uppercase;
    }

    .nav a::after {
        content: '';
        position: absolute;
        left: 0;
        bottom: 0;
        height: 2px;
        width: 100%;
        background: var(--color-accent);
        transform: scaleX(0);
        transform-origin: left;
        transition: transform var(--transition-fast);
    }

    .nav a:hover::after,
    .nav a:focus::after,
    .nav a.active::after {
        transform: scaleX(1);
    }

    .nav a:hover,
    .nav a:focus,
    .nav a.active {
        color: var(--color-accent-soft);
    }

    .burger {
        display: none;
        background: transparent;
        border: 1px solid var(--color-accent-soft);
        border-radius: var(--radius-sm);
        color: var(--text-primary);
        padding: 0.4rem 0.7rem;
    }

    @media (max-width: 760px) {
        .nav {
            justify-self: end;
            position: relative;
        }

        .nav ul {
            display: none;
            position: absolute;
            top: calc(100% + 10px);
            right: 0;
            flex-direction: column;
            min-width: 150px;
            align-items: center;
            background: var(--color-panel);
            padding: var(--space-sm);
            border: 1px solid var(--color-line);
            border-radius: var(--radius-md);
            z-index: 10;
        }

        .nav ul.open {
            display: flex;
        }

        .burger {
            display: inline-flex;
        }

        .nav a {
            width: 100%;
            justify-content: center;
        }

        .nav-item {
            transform: translateX(20px);
            animation: fadeLeft 0.4s ease forwards;
        }
    }

    @keyframes fadeUp {
        from { opacity: 0; transform: translateY(10px); }
        to { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeLeft {
        from { opacity: 0; transform: translateX(20px); }
        to { opacity: 1; transform: translateX(0); }
    }
</style>
