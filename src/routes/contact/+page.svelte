<script>
    const Contact = [
        {id: 1, name: "Call us", text: "555-123-4567"},
        {id: 2, name: "Email us", text: "carlowtourism@email.com"},
    ];
</script>

<svelte:head>
    <title>Contact Us</title>
</svelte:head>

<div class="contact-page">
    <div class="top-bar">
        <h1>Contact Us</h1>
    </div>

    <section class="contact-section">
        <div class="mobile">
            {#each Contact.slice(0, 2) as item}
                <div class="grid">
                    <h3>{item.name}</h3>
                    <p class="review">{item.text}</p>
                </div>
            {/each}
        </div>

        <div class="desktop">
            {#each Contact.slice(0, 2) as item}
                <div class="grid">
                    <h2>{item.name}</h2>
                    <p class="review">{item.text}</p>
                </div>
            {/each}
        </div>
    </section>
</div>

<style>
    .mobile {
        display: none;
    }

    .desktop {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: var(--space-xl);
        align-items: start;
    }

    .grid {
        border: 1px solid;
        padding: var(--space-sm) var(--space-lg) var(--space-xl);
    }

    .contact-page {
        max-width: 1600px;
        margin: 0 auto;
        padding: var(--space-sm) var(--space-lg) var(--space-xl);
    }

    .top-bar {
        text-align: center;
        margin-bottom: var(--space-sm);
        padding-bottom: var(--space-sm);
        border-bottom: 1px solid var(--color-border);
    }

    h1 {
        font-size: var(--font-xxl);
        margin: 0;
    }

    .contact-section {
        text-align: center;
        margin-bottom: var(--space-xl);
        padding-top: var(--space-xs);
    }

    @media (max-width: 1024px) {
        .desktop {
            display: none;
        }
        
        .mobile {
            display: grid;
            grid-template-columns: repeat(1, 1fr);
            gap: var(--space-xl);
            align-items: start;
        }
    }
</style>