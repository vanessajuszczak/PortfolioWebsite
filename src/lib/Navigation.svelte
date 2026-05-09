<script>
    import { page } from '$app/state';
    import {asset, resolve} from '$app/paths';
    
    

    const mainNavigationItems = [
        { name: 'About', path: '/about/' },
        { name: 'Projects', path: '/projects/' },
        { name: 'CV', path: '/cv/' }
    ];

    const contactNavigationItem = { name: 'Contact', path: '/contact/' };

    let isOpen = false;

    function hideMenu() {
        isOpen = false;
    }
</script>


<nav class="nav" aria-label="Main navigation">
    <a href={resolve('/')} class="logo-area">
        <img src={asset("/logo.png")} alt="Site Logo" />
    </a>

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
        {#each mainNavigationItems as item}
            <li class="nav-item">
                <a 
                    href={resolve(item.path)}
                    class:active={page.url.pathname === resolve(item.path)}
                    on:click={hideMenu}
                >{item.name}</a>
            </li>
        {/each}

        <li class="nav-item mobile-contact">
            <a href={resolve(contactNavigationItem.path)}
            class:active={page.url.pathname === resolve(contactNavigationItem.path)}
            on:click={hideMenu}>
                {contactNavigationItem.name}
            </a>
        </li>
    </ul>

    <div class="contact-nav">
        <a href={resolve(contactNavigationItem.path)} class="contact-button">
            {contactNavigationItem.name}
        </a>
    </div>
</nav>


<style>
    .nav {
        display: grid;
        grid-template-columns: 1fr auto 1fr;
        align-items: center;
        width: 100%;
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

    #main-menu {
        justify-self: center;
    }

    .contact-nav {
        justify-self: end;
    }

    .contact-button {
        border: 2px solid var(--color-accent-soft);
        border-radius: var(--radius-md);
        padding: 0.4rem 0.8rem;
    }

    .nav ul {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: var(--space-xl);
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
        font-size: var(--font-md);
        font-weight: 700;
        color: var(--text-primary);
        text-transform: uppercase;
    }

    .nav-item a::after {
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

    .nav-item a:hover::after,
    .nav-item a:focus::after,
    .nav-item a.active::after {
        transform: scaleX(1);
    }

    .nav-item a:hover,
    .nav-item a:focus,
    .nav-item a.active {
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

    .mobile-contact {
        display: none;
    }

    @media (max-width: 760px) {
        .nav {
            grid-template-columns: 1fr auto;
            position: relative;
        }

        .nav ul {
            display: none;
            position: absolute;
            top: 55px;
            right: 0;
            width: 220px;
            flex-direction: column;
            gap: var(--space-md);
            align-items: flex-end;
            background: var(--color-panel);
            padding: var(--space-md);
            border: 1px solid var(--color-line);
            border-radius: var(--radius-md);
            z-index: 20;
        }

        .nav ul.open {
            display: flex;
        }

        .burger {
            display: inline-flex;
            justify-content: center;
            align-items: center;
            border: 0;
            font-size: var(--font-xl);
            color: var(--text-primary);
            background: transparent;
        }

        .nav a {
            font-size: var(--font-lg);
            justify-content: flex-end;
        }

        .mobile-contact {
            display: block;
        }

        .contact-nav {
            display: none;
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
