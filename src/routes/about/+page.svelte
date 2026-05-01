
    <script>
    
    import { base } from '$app/paths';

    
</script>

<!-- TITLE -->
<h1 class="title">About This Website</h1>

<!-- MAIN SECTION -->
<div class="about-container">

  <!-- LEFT SIDE TEXT -->
  <div class="about-text">
    <h2>Welcome to Carlow </h2>
    <p>
    Carlow is a beautiful town in the southeast of Ireland, known for its rich history,
    scenic landscapes, and vibrant culture. It offers a perfect mix of heritage sites,
    outdoor activities, and modern attractions.
    </p>
    <p>
    Whether you are visiting for a short trip or planning a longer stay, Carlow has
    something for everyone — from historic castles to peaceful gardens and exciting
    entertainment venues.
  </p>

  <h3>Top Attractions</h3>
  <ul>
    <li>Altamont Gardens – famous for its stunning natural beauty</li>
    <li>Brownshill Dolmen – one of the largest dolmens in Ireland</li>
    <li>Carlow Castle – a historic Norman castle in the town centre</li>
    <li>The Dome – a popular entertainment centre</li>
  </ul>

    <h3>What you can do:</h3>
    <ul>
      <li>Explore cultural and historical landmarks</li>
    <li>Enjoy shopping and dining experiences</li>
    <li>Visit parks and nature trails</li>
    <li>Plan your own travel itinerary</li>
    </ul>

    
    <h3>About This Project</h3>
  <p>
    This website was developed as part of a college project in Computing in Interactive
    Digital Art and Design. The aim is to create a user-friendly travel guide that helps
    visitors easily discover places and plan their visit to Carlow.
  </p>

    <a href=" {base}/" class="btn">Back to Home</a>
  </div>

  <!-- RIGHT SIDE IMAGE -->
  <div class="about-image">
    <img src=" {base}/images/about/Carlow.jpg" alt="Carlow town view landscape" />
  </div>

</div>

<style>
/* TITLE CENTER */
.title {
  text-align: center;
  font-size: 32px;
  margin-bottom: 30px;
  margin-top: 50px;
}

/* MAIN LAYOUT */
.about-container {
  display: flex;
  align-items:center;
  justify-content: space-between;
  gap: 50px;
  margin: auto;
  padding: 20px 40px;
  padding-left: 40px;
}

/* LEFT TEXT */
.about-text {
  flex: 1;
  margin-top: 60px;
}

.about-text p {
  margin-bottom: 10px;
  color: #444;
}

.about-text ul {
  margin: 10px 0;
}

/* RIGHT IMAGE */
.about-image {
  flex: 1;
  margin-top: -30px;
}

.about-image img {
  width: 100%;
  border-radius: 10px;
  object-fit: cover;
}

/* BUTTON */
.btn {
  display: inline-block;
  margin-top: 20px;
  background: #2e7d32;
  color: white;
  padding: 10px 16px;
  border-radius: 6px;
  text-decoration: none;
}

/* MOBILE RESPONSIVE */
@media (max-width: 768px) {
  .about-container {
    flex-direction: column;
  }
}
</style>