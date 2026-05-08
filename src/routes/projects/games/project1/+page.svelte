<script>
    import {base} from '$app/paths';
</script>

<section class="project-page">
    <div class="hero-image">
        <img src={base + '/images/games/project1/main.png'} alt="Game 1 Screenshot" />
    </div>

    <div class="project-info">
        <h1>Shopping Collection Game</h1>

        <p class="project-desc">
            The player must add items from their shopping list to the cart.
        </p>

        <div class="project-details">
            <p><strong>Software:</strong> Visual Studio 2022</p>
            <p><strong>Year:</strong> 2025</p>
        </div>
    </div>
</section>

<div class="gallery">
    <h2>Gallery</h2>

    <div class="gallery-grid">
        <img src={base + '/images/games/project1/ss1.png'} alt="Screenshot" />
        <img src={base + '/images/games/project1/ss2.png'} alt="Screenshot" />
        <img src={base + '/images/games/project1/ss3.png'} alt="Screenshot" />
    </div>
</div>

<style>
    .project-page {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: var(--space-xl);

        padding: var(--space-xl);
        align-items: center;
    }

    .hero-image img {
        width: 100%;
        border-radius: var(--radius-md);
        border: 2px solid var(--color-line);
    }
    
    .project-info h1 {
        margin-bottom: var(--space-md);
        font-size: var(--font-xxl);
    }

    .project-desc {
        margin-bottom: var(--space-lg);
        font-size: var(--font-lg);
    }

    .project-details {
        display: grid;
        gap: var(--space-sm);
    }

    .gallery {
        margin-top: var(--space-lg);
        text-align: center;
        margin-bottom: var(--space-xl);
    }

    .gallery h2 {
        margin-bottom: var(--space-md);
        font-size: var(--font-xxl);
    }

    .gallery-grid {
        display: flex;
        justify-content: center;
        gap: var(--space-md);
        flex-wrap: wrap;
    }

    .gallery-grid img {
        width: 350px;
        max-width: 100%;
        border-radius: var(--radius-md);
        border: 2px solid var(--color-line);
        object-fit: cover;
    }

    @media (min-width: 1300px) {
        .gallery-grid img {
            width: 450px;
        }

        .gallery h2 {
            font-size: var(--font-xxxl);
        }

        .project-desc {
            font-size: var(--font-xl);
        }

        .project-details {
            font-size: var(--font-lg);
        }
    }
</style>