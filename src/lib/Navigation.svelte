<script>
    import { page } from '$app/state';
    import {resolve} from '$app/paths';
    

    const navigationItems = [
        { name: 'About', path: '/about/' },
        { name: 'Things to Do', path: '/things-to-do/' },
        { name: 'Guides', path: '/guides/' },
        { name: 'User Reviews', path: '/user-reviews/' },
        { name: 'Contact Us', path: '/contact/' }
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
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        gap: var(--space-lg);
        animation: fadeIn var(--transition-slow);
        position: relative;
    }

    .nav ul {
        display: flex;
        flex-wrap: wrap;
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
    .nav-item:nth-child(5) { animation-delay: 1s; }

    .nav a {
        position: relative;
        display: block;
        font-family: var(--font-body);
        font-size: var(--font-lg);
        font-weight: 600;
        color: var(--text-contrast);
        padding: var(--space-xs) var(--space-sm);
        text-decoration: none;
        transition: color var(--transition-fast);
        white-space: nowrap;
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
        color: var(--color-accent);
    }

    .burger {
        display: none;
        font-size: var(--font-xl);
        background: none;
        border: none;
        color: var(--text-contrast);
        padding: var(--space-xs);
        cursor: pointer;
        margin: 0;
    }

    @media (max-width: 1024px) {
        .nav {
            width: auto;
            margin-left: auto;
        }

        .nav ul {
            display: none;
            position: absolute;
            top: calc(100% + 8px);
            right: 0;
            flex-direction: column;
            gap: var(--space-sm);
            min-width: 220px;
            background: var(--color-secondary);
            padding: var(--space-sm);
            border-radius: var(--radius-md);
            box-shadow: var(--shadow-md);
            z-index: 200;
        }

        .nav ul.open {
            display: flex;
        }

        .burger {
            display: block;
        }

        .nav li,
        .nav a {
            width: 100%;
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
