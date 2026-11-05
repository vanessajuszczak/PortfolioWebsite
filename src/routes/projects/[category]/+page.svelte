<script>
    import {base} from '$app/paths';
    import ProjectCard from '$lib/components/ProjectCard.svelte';

    export let params;

    const category = params.category;

    const projectData = {
        games: [
            {title: 'The Eyes Path', description: 'Developed as a group project for the Animation Dingle 2027 Game Sting Competition.', href: base + '/projects/games/project1', image: base + '/images/games/project1/thumbnail.png'},
            {title: 'The Descent', description: 'Advance through the floors, defeat the monster, and find a way to escape!', href: base + '/projects/games/project2', image: base + '/images/games/project2/main.png'},
            {title: 'Midnight Mayhem', description: 'Survive the night, battle waves of enemies, and aim for the highest score!', href: base + '/projects/games/project3', image: base + '/images/games/project3/game.png'},
            {title: 'Side Scrolling Shooter Game', description: 'The player must shoot enemies to reach a score of 50.', href: base + '/projects/games/project4', image: base + '/images/games/project4/main.png'},
            {title: 'Shopping Collection Game', description: 'The player must add items from their shopping list to the cart.', href: base + '/projects/games/project5', image: base + '/images/games/project5/main.png'}
        ],
        'digital-art': [
            {title: 'Places I Never Left', description: 'An original zine design exploring fictional places that still feel like home, using a scrapbook-inspired aesthetic.', href: base + '/projects/digital-art/project1', image: base + '/images/digital-art/project1/thumbnail.png'},
            {title: 'Visual Clock Design', description: 'Digital animations exploring different visual designs for a clock, ultimately settling for a flower design.', href: base + '/projects/digital-art/project2', image: base + '/images/digital-art/project2/currentFlower.gif'},
            {title: 'Productive Website Wireframes', description: ' A collection of website wireframes outlining the layout and interface of a productivity-focused website.', href: base + '/projects/digital-art/project3', image: base + '/images/digital-art/project3/thumbnail.png'},
            {title: 'Carlow Tourism Website', description: 'A website developed to showcase Carlows attractions, activities and local visitor information.', href: base + '/projects/digital-art/project4', image: base + '/images/digital-art/project4/1.png'},
            {title: 'Portfolio Website Wireframes', description: 'Wireframes outlining the layout and structure of this personal portfolio website.', href: base + '/projects/digital-art/project5', image: base + '/images/digital-art/project5/thumbnail.png'},
            {title: 'Original Character Design & Walk Cycle Animation', description: 'Original red panda character design featuring a character turnaround sheet and a walk cycle animation.', href: base + '/projects/digital-art/project6', image: base + '/images/digital-art/project6/turnaround.png'},
            {title: 'Head-turn Animation', description: 'An animation showcasing an original characters head-turn with changing facial expressions.', href: base + '/projects/digital-art/project7', image: base + '/images/digital-art/project7/gif3.gif'},
            {title: 'Basic Animations', description: 'A collection of beginner animations exploring movement and animation principles through a bouncing ball, water and fire.', href: base + '/projects/digital-art/project8', image: base + '/images/digital-art/project8/gif1.gif'},
            {title: 'Fantasy Game Original Character', description: 'Concept art of an original character designed for a fantasy-style game.', href: base + '/projects/digital-art/project9', image: base + '/images/digital-art/project9/ss1.png'},
            {title: 'Pixel Art Game Assets Project', description: 'A collection of original pixel art assets created for a 2D adventure game as part of my Concept Art for Games module, including characters, environments and game elements.', href: base + '/projects/digital-art/project10', image: base + '/images/digital-art/project10/thumbnail.gif'},
            {title: 'Pixel Art Sprites Collection', description: 'A collection of original 2D pixel art sprites.', href: base + '/projects/digital-art/project11', image: base + '/images/digital-art/project11/ball.gif'},
            {title: 'Digital Art Studies & Fan Art', description: 'A collection of digital art studies and fan art, featuring texture experiments, character sketches and finished illustrations.', href: base + '/projects/digital-art/project12', image: base + '/images/digital-art/project12/thumbnail.png'},
            {title: 'Figma Assignment App Prototype', description: 'An interactive Figma prototype for a teacher-focused app designed to manage assignments and student submissions.', href: base + '/projects/digital-art/project13', image: base + '/images/digital-art/project13/figma.png'},
            {title: 'Character & Companion Design', description: 'Concept art and character designs for Luna and her dragon companion, exploring their visual identities and fantasy-inspired original designs.', href: base + '/projects/digital-art/project14', image: base + '/images/digital-art/project14/luna2.png'}
        ],
        '3d': [
            {title: '3D Game Asset', description: 'A 3D model of a tube slide used as a finish goal in a game.', href: base + '/projects/3d/project1', image: base + '/images/3d/project1/main.jpg'},
            {title: 'School Bus Model', description: 'A 3D model of a school bus with custom UV-mapping.', href: base + '/projects/3d/project2', image: base + '/images/3d/project2/main.jpg'},
            {title: 'Random Basic 3D Models', description: 'A compilation of random 3D models, including scaffolding, a castle, a mug, and hands.', href: base + '/projects/3d/project3', image: base + '/images/3d/project3/main.jpg'}
        ]
    };

    const categoryTitles = {
        games: 'Games',
        'digital-art': 'Digital Art',
        '3d': '3D Models'
    };

    const projects = projectData[category] || [];
</script>

<section class="category-page">
    <h1>{categoryTitles[category]}</h1>

    <div class="grid">
        {#each projects as project}
            <ProjectCard
                title={project.title}
                description={project.description}
                href={project.href}
                image={project.image}
            />
        {/each}
    </div>

    <p class="mobile-scroll-hint">Scroll to View Projects ➜</p>
</section>

<style>
    .category-page {
        text-align: center;
        padding: var(--space-xl);
    }

    .grid {
        display: flex;
        justify-content: flex-start;
        gap: var(--space-lg);
        
        overflow-x: auto;
        overflow-y: hidden;
        width: 100%;

        padding: var(--space-md);
        scroll-snap-type: x mandatory;
    }

    .grid::-webkit-scrollbar {
        height: 10px;
    }

    .grid::-webkit-scrollbar-track {
        background: var(--color-purple-bottom);
        border-radius: var(--radius-md);
    }

    .grid::-webkit-scrollbar-thumb {
        background: var(--color-accent);
        border-radius: var(--radius-md);
    }

    :global(.project-card) {
        flex: 0 0 31%;

        max-width: 360px;
        min-width: 300px;
        scroll-snap-align: center;
    }
    
    .category-page h1 {
        font-size: var(--font-xxl);
        margin-bottom: 0;
    }

    .mobile-scroll-hint {
        display: none;
    }

    @media (max-width: 760px) {
        .grid {
            padding-bottom: var(--space-sm);
            scrollbar-width: thin;
            scrollbar-color: var(--color-accent) var(--color-purple-bottom);
        }

        .grid::-webkit-scrollbar {
            height: 10px;
        }

        .grid::-webkit-scrollbar-track {
            background: var(--color-purple-bottom);
            border-radius: var(--radius-md);
        }

        .grid::-webkit-scrollbar-thumb {
            background: var(--color-accent);
            border-radius: var(--radius-md);
        }

        .mobile-scroll-hint {
            display: block;
            margin: var(--space-sm) auto var(--space-lg);
            margin-top: var(--space-lg);
            color: var(--text-secondary);
            font-size: var(--font-md);
            font-weight: 700;
            text-align: center;
            text-transform: uppercase;
        }
        .category-page {
            padding: 60px var(--space-lg) var(--space-md);
        }

        .category-page h1 {
            margin-bottom: var(--space-lg);
        }

        .grid {
            padding: 0 0 var(--space-lg);
            gap: var(--space-md);
        }
    }

    @media (min-width: 1300px) {
        :global(.project-card) {
            max-width: 620px;
        }
        .category-page h1 {
        font-size: var(--font-xxxl);
    }
    }
</style>