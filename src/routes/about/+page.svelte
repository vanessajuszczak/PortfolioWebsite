<script>
    import { base } from '$app/paths';

    const skills = [
        'UI/UX Design',
        'Game Development',
        'Digital Illustration',
        'Animation',
        '3D Modelling',
        'Responsive Web Design'
    ];
</script>

<section class="about-page">
    <div class="about-layout">
        <div class="about-image">
            <img src={base + '/images/about/about-image.jpg'} alt="About img" />
        </div>

        <div class="about-content">
            <h1>About Me</h1>

            <p>
                Hi, I'm Vanessa, an Interactive Digital Art and Design student with
                an interest in digital media, game development, and user-focused design.
                My work combines creativity with development across areas including 
                games, animation, illustration, and 3D modelling.
            </p>

            <p>
                I focus on creating visually engaging experiences in my projects, 
                while also improving usability and interaction design.
            </p>

            <div class="skills-section">
                <h2>My Skills</h2>

                <ul>
                    {#each skills as skill}
                        <li>{skill}</li>
                    {/each}
                </ul>
            </div>
        </div>
    </div>
</section>

<style>
    .about-page {
        padding: var(--space-xl);
    }

    .about-layout {
        display: grid;
        grid-template-columns: 350px 1fr;
        gap: var(--space-xl);
        align-items: start;

        max-width: 1400px;
        margin: 0 auto;
    }

    .about-image img {
        width: 100%;
        border-radius: var(--radius-md);
        border: 2px solid var(--color-line);
    }

    .about-content h1 {
        margin-bottom: var(--space-md);
        font-size: var(--font-xxxl);
    }

    .about-content p {
        margin-bottom: var(--space-md);
        font-size: var(--font-lg);
        line-height: 1.8;
    }

    .skills-section {
        margin-top: var(--space-lg);
    }

    .skills-section h2 {
        margin-bottom: var(--space-md);
        font-size: var(--font-xxl);
    }

    .skills-section ul {
        display: grid;
        gap: var(--space-sm);

        padding: 0;
        list-style: none;
    }

    .skills-section li {
        position: relative;
        padding-left: 28px;
        font-size: var(--font-lg);
    }

    .skills-section li::before {
        content: '✔';
        position: absolute;
        left: 0;
        color: var(--color-accent);
    }

    @media (max-width: 900px) {
        .about-layout {
            grid-template-columns: 1fr;
        }

        .about-image {
            max-width: 350px;
            margin: 0 auto;
        }

        .about-content {
            text-align: center;
        }

        .skills-section li {
            padding-left: 0;
        }

        .skills-section li::before {
            position: static;
            margin-right: 8px;
        }
    }

    @media (min-width: 1300px) {
        .about-layout {
            grid-template-columns: 420px 1fr;
        }

        .about-content p {
            font-size: var(--font-xl);
        }

        .skills-section li {
            font-size: var(--font-xl);
        }
    }
</style>