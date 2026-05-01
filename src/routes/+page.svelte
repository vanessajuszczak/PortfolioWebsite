<svelte:head>
    <title>Carlow Tourism</title>
</svelte:head>

<script>
    import { resolve, asset } from '$app/paths';
   const siteSections = [
    {
        title: 'Things to Do',
        text: 'Browse activities, attractions, shopping places, and popular places across Carlow.',
        link: resolve('/things-to-do/'),
        image: asset('/images/homepage/things-to-do.png')
    },
    {
        title: 'Guides',
        text: 'Read useful, local guides to help plan your visit and discover more of Carlow.',
        link: resolve('/guides/'),
        image: asset('/images/homepage/guides.png')
    },
    {
        title: 'User Reviews',
        text: 'See what visitors think and explore experiences shared by other people.',
        link: resolve('/user-reviews/'),
        image: asset('/images/homepage/user-reviews.png')
    }
   ];

   const featuredHighlights = [
    {
        title: 'Brownshill Portal Dolmen',
        image: asset('/images/things-to-do/popular-places/dolmen.png')
    },
    {
        title: 'The Dome Entertainment Centre',
        image: asset('/images/things-to-do/entertainment/dome.png')
    },
    {
        title: 'Carlow Castle',
        image: asset('/images/things-to-do/popular-places/castle.png')
    }
   ];
</script>

<!-- Page Container -->
<div class="home-container">
    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <h1>Carlow</h1>
            <p class="hero-text">
                Discover activities, local guides, and visitor reviews to help you plan your trip around Carlow.
            </p>
            <a class="hero-button" href="#explore">Start Exploring</a>
        </div>
    </section>

    <!-- Explore Section -->
    <section class="explore-section" id="explore">
        <h2>Explore the Website</h2>

        <div class="section-grid">
            {#each siteSections as item}
                <div class="section-card">
                    <img src={item.image} alt={item.title} class="section-image" />
                    <h3>{item.title}</h3>
                    <p>{item.text}</p>
                    <a class="section-button" href={item.link}>Explore</a>
                </div>
            {/each}
        </div>
    </section>

    <!-- Highlights Section -->
     <section class="highlights-section">
        <h2>Featured Highlights</h2>

        <div class="highlights-grid">
            {#each featuredHighlights as item}
                <div class="highlight-card">
                    <img src={item.image} alt={item.title} class="highlight-image" />
                    <h3>{item.title}</h3>
                </div>
            {/each}
        </div>

        <a class="highlights-button" href={resolve('/things-to-do/')}>GO</a>
     </section>

     <!-- Plan Visit Section -->
      <section class="visit-section">
        <h2>Plan Your Visit</h2>
        <p> Looking for more information before your trip? 
            See our contact page and start planning your visit to Carlow.
        </p>
        <a class="visit-button" href={resolve('/contact/')}>Contact Us</a>
      </section>
</div>


<style>
    .home-container {
        display: flex;
        flex-direction: column;
        gap: var(--space-xl);
    }

    /* Hero Section */
    .hero {
        text-align: center;
        min-height: 85vh;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: var(--space-xl) var(--space-md);
        border-radius: var(--radius-md);
        background-image: url('/images/backgrounds/carlow-hero.png');
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        background-blend-mode: overlay;
        background-color: rgba(255, 255, 255, 0.75);
    }

    .hero-content {
        max-width: 800px;
        margin: 0 auto;
    }

    .hero h1 {
        font-size: var(--font-xxl);
        margin-bottom: var(--space-sm);
    }

    .hero-text {
        font-size: var(--font-lg);
        margin-bottom: var(--space-md);
    }

    .hero-button {
        display: inline-block;
        background-color: var(--color-primary);
        color: var(--text-contrast);
        padding: var(--space-sm) var(--space-lg);
        border-radius: var(--radius-sm);
        font-weight: 600;
    }

    .hero-button:hover,
    .hero-button:focus {
        background-color: var(--color-secondary);
    }

    /* Explore, Highlights, and Plan Visit Section */
    .explore-section,
    .highlights-section,
    .visit-section {
        padding: var(--space-xl) var(--space-md);
        text-align: center;
    }
    
    .explore-section h2,
    .highlights-section h2,
    .visit-section h2 {
        margin-bottom:  var(--space-lg);
    }

    .section-grid,
    .highlights-grid {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: var(--space-lg);
    }

    .section-card,
    .highlight-card {
        background-color: var(--color-background);
        border: 1px solid var(--color-border);
        border-radius: var(--radius-md);
        padding: var(--space-md);
        box-shadow: var(--shadow-sm);
    }

    .section-image,
    .highlight-image {
        width: 100%;
        height: 220px;
        object-fit: cover;
        border-radius: var(--radius-sm);
        margin-bottom: var(--space-sm);
    }

    .section-card h3,
    .highlight-card h3 {
        margin-bottom: var(--space-sm);
    }

    .section-card p {
        margin-bottom: var(--space-md);
    }

    .section-button,
    .visit-button {
        display: inline-block;
        background-color: var(--color-primary);
        color: var(--text-contrast);
        padding: var(--space-sm) var(--space-md);
        border-radius: var(--radius-sm);
        font-weight: 600;
    }

    .highlights-button {
        display: inline-block;
        width: 150px;
        margin-top: var(--space-lg);
        background-color: var(--color-primary);
        color: var(--text-contrast);
        padding: var(--space-sm) var(--space-lg);
        border-radius: var(--radius-sm);
        font-weight: 600;
    }

    .section-button:hover,
    .section-button:focus,
    .visit-button:hover,
    .visit-button:focus,
    .highlights-button:hover,
    .highlights-button:focus {
        background-color: var(--color-secondary);
    }

    .visit-section {
        max-width: 800px;
        margin: 0 auto;
    }

    .visit-section p {
        margin-bottom: var(--space-md);
    }
    
    @media (max-width: 1024px) {
        .section-grid,
        .highlights-grid {
            grid-template-columns: 1fr;
        }

        .section-image,
        .highlight-image {
            height: 200px;
        }
    }
</style>
