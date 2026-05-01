<script>
    import { asset } from '$app/paths';

    const entertainmentItems = [
        { id: 1, name: 'IMC Cinema', image: asset('/images/things-to-do/entertainment/imc-cinema.png') },
        { id: 2, name: 'The Dome Entertainment Centre', image: asset('/images/things-to-do/entertainment/dome.png') },
        { id: 3, name: 'Graiguecullen Swimming Pool', image: asset('/images/things-to-do/entertainment/pool.png') },
        { id: 4, name: 'The Foundry Nightclub', image: asset('/images/things-to-do/entertainment/foundry.png') }
    ];

    const popularPlacesItems = [
        { id: 5, name: 'Brownshill Portal Dolmen', image: asset('/images/things-to-do/popular-places/dolmen.png') },
        { id: 6, name: 'Carlow County Museum', image: asset('/images/things-to-do/popular-places/museum.png') },
        { id: 7, name: 'Carlow Castle', image: asset('/images/things-to-do/popular-places/castle.png') },
        { id: 8, name: "Duckett's Grove", image: asset('/images/things-to-do/popular-places/ducketts-grove.png') }
    ];

    const shoppingItems = [
        { id: 9, name: 'Carlow Shopping Centre', image: asset('/images/things-to-do/shopping/carlow-sc.png') },
        { id: 10, name: 'Fairgreen Shopping Centre', image: asset('/images/things-to-do/shopping/fairgreen-sc.png') },
        { id: 11, name: 'Penneys', image: asset('/images/things-to-do/shopping/penneys.png') },
        { id: 12, name: 'Haddens Centre', image: asset('/images/things-to-do/shopping/haddens-centre.png') }
    ];

    let selectedCategory = '';
    let selectedActivity = '';
    let savedActivities = [];

    let editingId = null;
    let editCategory = '';
    let editActivity = '';

    function getActivitiesForCategory() {
        if(selectedCategory === 'Entertainment') {
            return entertainmentItems;
        }

        if(selectedCategory === 'Popular Places') {
            return popularPlacesItems;
        }

        if(selectedCategory === 'Shopping') {
            return shoppingItems;
        }

        return [];
    }

    function getAvailableActivities() {
        let categoryActivities = getActivitiesForCategory();
        let availableActivities = [];

        for (let i = 0; i < categoryActivities.length; i++) {
            let alreadySaved = false;

            for (let j = 0; j < savedActivities.length; j++) {
                if(savedActivities[j].name === categoryActivities[i].name) {
                    alreadySaved = true;
                }
            }

            if (alreadySaved === false) {
                availableActivities.push(categoryActivities[i]);
            }
        }

        return availableActivities;
    }

    function handleCategoryChange() {
        selectedActivity = '';
    }

    function addActivity() {
        if (selectedCategory === '' || selectedActivity === '') {
            return;
        }

        savedActivities.push({
            id: Date.now(),
            name: selectedActivity,
            category: selectedCategory
        });

        savedActivities = savedActivities;
        selectedCategory = '';
        selectedActivity = '';
    }

    function deleteActivity(id) {
        let confirmedDelete = confirm('Delete this saved activity?');

        if(confirmedDelete === false) {
            return;
        }

        for (let i = 0; i < savedActivities.length; i++) {
            if (savedActivities[i].id === id) {
                savedActivities.splice(i, 1);
                break;
            }
        }

        savedActivities = savedActivities;
    }

    function getAvailableActivitiesForEdit() {
        let categoryActivities = [];

        if (editCategory === 'Entertainment') {
            categoryActivities = entertainmentItems;
        }

        if (editCategory === 'Popular Places') {
            categoryActivities = popularPlacesItems;
        }

        if (editCategory === 'Shopping') {
            categoryActivities = shoppingItems;
        }

        let availableActivities = [];

        for (let i = 0; i < categoryActivities.length; i++) {
            let alreadySaved = false;

            for (let j = 0; j < savedActivities.length; j++) {
                if (savedActivities[j].name === categoryActivities[i].name &&
                    savedActivities[j].id !== editingId) {
                    alreadySaved = true;
                }
            }

            if (alreadySaved === false) {
                availableActivities.push(categoryActivities[i]);
            }
        }

        return availableActivities;
    }

    function startEdit(activity) {
        editingId = activity.id;
        editCategory = activity.category;
        editActivity = activity.name;
    }

    function handleEditCategoryChange() {
        editActivity = '';
    }

    function saveEdit(id) {
        if(editCategory === '' || editActivity === '') {
            return;
        }

        for (let i = 0; i < savedActivities.length; i++) {
            if(savedActivities[i].id === id) {
                savedActivities[i].category = editCategory;
                savedActivities[i].name = editActivity;
                break;
            }
        }

        savedActivities = savedActivities;
        editingId = null;
        editCategory = '';
        editActivity = '';
    }

    function cancelEdit() {
        editingId = null;
        editCategory = '';
        editActivity = '';
    }
</script>

<svelte:head>
    <title>Things to Do</title>
</svelte:head>

<div class="things-page">
    <div class="top-bar">
        <h1>Things to Do</h1>
    </div>

    <section class="category-section">
        <h2>Entertainment</h2>

        <div class="card-grid desktop-cards">
            {#each entertainmentItems.slice(0, 3) as item}
                <div class="activity-card">
                    <img src={item.image} alt={item.name} class="activity-image" />
                    <p class="activity-name">{item.name}</p>
                    <button class="go-button" aria-label="Go to activity page">GO</button>
                </div>
            {/each}
        </div>

        <div class="mobile-card">
            <div class="activity-card">
                <img src={entertainmentItems[0].image} alt={entertainmentItems[0].name} class="activity-image" />
                <p class="activity-name">{entertainmentItems[0].name}</p>
                <button class="go-button" aria-label="Go to activity page">GO</button>
            </div>
        </div>

        <button class="view-all-button" aria-label="View all entertainment activities">View All →</button>
    </section>

    <section class="category-section">
        <h2>Popular Places</h2>

        <div class="card-grid desktop-cards">
            {#each popularPlacesItems.slice(0, 3) as item}
                <div class="activity-card">
                    <img src={item.image} alt={item.name} class="activity-image" />
                    <p class="activity-name">{item.name}</p>
                    <button class="go-button" aria-label="Go to activity page">GO</button>
                </div>
            {/each}
        </div>

        <div class="mobile-card">
            <div class="activity-card">
                <img src={popularPlacesItems[0].image} alt={popularPlacesItems[0].name} class="activity-image" />
                <p class="activity-name">{popularPlacesItems[0].name}</p>
                <button class="go-button" aria-label="Go to activity page">GO</button>
            </div>
        </div>

        <button class="view-all-button" aria-label="View all popular places">View All →</button>
    </section>

    <section class="category-section">
        <h2>Shopping</h2>

        <div class="card-grid desktop-cards">
            {#each shoppingItems.slice(0, 3) as item}
                <div class="activity-card">
                    <img src={item.image} alt={item.name} class="activity-image" />
                    <p class="activity-name">{item.name}</p>
                    <button class="go-button" aria-label="Go to activity page">GO</button>
                </div>
            {/each}
        </div>

        <div class="mobile-card">
            <div class="activity-card">
                <img src={shoppingItems[0].image} alt={shoppingItems[0].name} class="activity-image" />
                <p class="activity-name">{shoppingItems[0].name}</p>
                <button class="go-button" aria-label="Go to activity page">GO</button>
            </div>
        </div>

        <button class="view-all-button" aria-label="View all shopping activities">View All →</button>
    </section>

    <section class="saved-section">
        <h2>Save an Activity</h2>

        <div class="saved-form">
            <div class="field">
                <label for="category-select">Category</label>
                <select id="category-select" bind:value={selectedCategory} on:change={handleCategoryChange}>
                    <option value="">Select a category</option>
                    <option value="Entertainment">Entertainment</option>
                    <option value="Popular Places">Popular Places</option>
                    <option value="Shopping">Shopping</option>
                </select>
            </div>

            {#if selectedCategory !== ''}
                <div class="field">
                    <label for="activity-select">Activity</label>
                    <select id="activity-select" bind:value={selectedActivity}>
                        <option value="">Select an activity</option>
                        {#each getAvailableActivities() as activity}
                            <option value={activity.name}>{activity.name}</option>
                        {/each}
                    </select>
                </div>
            {/if}

            <button class="primary-button" on:click={addActivity} aria-label="Save selected activity to list">Save to List</button>
        </div>

        <p class="saved-list-label">Your Saved Activities</p>

        {#if savedActivities.length === 0}
            <p class="empty-message">No saved activities yet.</p>
        {:else}
            <div class="saved-list">
                {#each savedActivities as activity}
                    <div class="saved-item">
                        {#if editingId === activity.id}
                            <div class="saved-text">
                                <div class="field">
                                    <label for="edit-category">Category</label>
                                    <select id="edit-category" bind:value={editCategory} on:change={handleEditCategoryChange}
                                    aria-label="Edit saved activity category">
                                        <option value="">Select a category</option>
                                        <option value="Entertainment">Entertainment</option>
                                        <option value="Popular Places">Popular Places</option>
                                        <option value="Shopping">Shopping</option>
                                    </select>
                                </div>

                                {#if editCategory !== ''}
                                    <div class="field">
                                        <label for="edit-activity">Activity</label>
                                        <select id="edit-activity" bind:value={editActivity}
                                        aria-label="Edit saved activity">
                                            <option value="">Select an activity</option>
                                            {#each getAvailableActivitiesForEdit() as item}
                                                <option value={item.name}>{item.name}</option>
                                            {/each}
                                        </select>
                                    </div>
                                {/if}
                            </div>

                            <div class="saved-actions">
                                <button class="primary-button" on:click={() => saveEdit(activity.id)}
                                aria-label="Save changes to saved activity">Save</button>
                                <button class="secondary-button" on:click={cancelEdit}
                                aria-label="Cancel editing saved activity">Cancel</button>
                            </div>
                        {:else}
                            <div class="saved-text">
                                <p class="saved-category">{activity.category}</p>
                                <p class="saved-name">{activity.name}</p>
                            </div>

                            <div class="saved-actions">
                                <button class="primary-button" on:click={() => startEdit(activity)}
                                aria-label="Edit saved activity">Edit</button>

                                <button class="secondary-button" on:click={() => deleteActivity(activity.id)}
                                aria-label="Delete activity from saved activities">Delete</button>
                            </div>
                        {/if}
                    </div>
                {/each}
            </div>
        {/if}
    </section>
</div>

<style>
    .things-page {
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

    .category-section {
        text-align: center;
        margin-bottom: var(--space-xl);
        padding-top: var(--space-xs);
    }

    .saved-section {
        margin-top: var(--space-xl);
        padding-top: var(--space-sm);
    }

    h2 {
        font-size: var(--font-xl);
        margin-bottom: var(--space-md);
        text-align: center;
    }

    .card-grid {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: var(--space-xl);
        align-items: start;
    }

    .mobile-card {
        display: none;
    }

    .desktop-cards {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: var(--space-xl);
        align-items: start;
    }

    .activity-card {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .activity-image {
        width: 300px;
        max-width: 100%;
        height: 220px;
        object-fit: cover;
        border: 1px solid var(--color-border);
        margin-bottom: var(--space-sm);
    }

    .activity-name {
        margin: 0 0 var(--space-xs);
        font-size: var(--font-base);
        text-align: center;
    }

    .go-button {
        background: var(--color-primary);
        color: var(--text-contrast);
        padding: var(--space-xs) var(--space-md);
        border-radius: var(--radius-sm);
        font-size: var(--font-sm);
        font-weight: 600;
        border: none;
    }

    .go-button:hover,
    .go-button:focus {
        background: var(--color-secondary);
    }

    .view-all-button {
        background: var(--color-background);
        color: var(--color-text);
        border: 1px solid var(--color-accent);
        padding: var(--space-xs) var(--space-md);
        border-radius: var(--radius-sm);
        font-size: var(--font-sm);
        font-weight: 500;
        margin-top: var(--space-sm);
    }

    .saved-form {
        display: flex;
        flex-direction: column;
        gap: var(--space-md);
        max-width: 500px;
        margin: 0 auto var(--space-lg);
    }

    .field {
        display: flex;
        flex-direction: column;
        gap: var(--space-xs);
    }

    .saved-list-label {
        text-align: center;
        font-weight: 600;
        margin-bottom: var(--space-md);
    }

    .saved-list {
        display: flex;
        flex-direction: column;
        gap: var(--space-sm);
        max-width: 500px;
        margin: 0 auto;
    }

    .saved-item {
        background-color: var(--color-background);
        border: 1px solid var(--color-border);
        border-radius: var(--radius-md);
        padding: var(--space-md);
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: var(--space-md);
    }

    .saved-text {
        display: flex;
        flex-direction: column;
        gap: var(--space-xs);
    }

    .saved-actions {
        display: flex;
        gap: var(--space-sm);
        flex-wrap: wrap;
    }

    .saved-name {
        margin: 0;
    }

    .saved-category {
        margin: 0;
        font-weight: 600;
        color: var(--color-secondary);
    }

    .empty-message {
        text-align: center;
    }

    @media (max-width: 1024px) {
        .things-page {
            padding: var(--space-sm);
        }

        .desktop-cards {
            display: none;
        }

        .mobile-card {
            display: flex;
            justify-content: center;
        }

        .activity-card {
            width: 100%;
            align-items: center;
        }

        .saved-item {
            flex-direction: column;
            align-items: flex-start;
        }

        .saved-actions {
            width: 100%;
        }
    }
</style>