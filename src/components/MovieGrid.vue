<template>
<section id="movies" class="container">
    <div class="header-section">
    <h2>Collect your favourites</h2>
    <div class="search-container">
        <svg class="search-icon" width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
        <path d="M15.5 14h-.79l-.28-.27C15.41 12.59 16 11.11 16 9.5 16 5.91 13.09 3 9.5 3S3 5.91 3 9.5 5.91 16 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
        </svg>
        <input
        type="text"
        v-model="query"
        @input="searchMovies"
        placeholder="Search title and add to grid"
        class="search-box"
        />
    </div>
    </div>
    
    <hr class="divider">

    <div class="movie-grid">
    <div
        class="movie-card"
        v-for="movie in movies"
        :key="movie.id"
    > 
        <div class="image-wrapper">
        <img
            :src="movie.image || placeholderImage"
            :alt="movie.name"
        />
        <div
            class="close-btn"
            @click="removeMovie(movie.id)"
        >
            ×
        </div>
        </div>
        <div class="card-content">
        <h3>{{ movie.name }}</h3>
        <p>{{ movie.summary }}</p>
        </div>
    </div>
    </div>
</section>
</template>

<script>
export default {
data() {
    return {
    movies: [],
    query: "",
    placeholderImage:
        "https://via.placeholder.com/300x450?text=No+Image",
    };
},
methods: {
    fetchInitialMovies() {
    fetch("https://api.tvmaze.com/shows")
        .then((res) => res.json())
        .then((data) => {
        this.movies = data.slice(0, 3).map((show) => ({
            id: show.id,
            name: show.name,
            image: show.image?.original || "",
            summary:
            show.summary?.replace(/<[^>]+>/g, "") || "",
        }));
        });
    },
    searchMovies() {
    if (!this.query.trim()) return;
    fetch(
        `https://api.tvmaze.com/search/shows?q=${this.query}`
    )
        .then((res) => res.json())
        .then((data) => {
        const newMovies = data
            .map((item) => item.show)
            .map((show) => ({
            id: show.id,
            name: show.name,
            image: show.image?.original || "",
            summary:
                show.summary?.replace(/<[^>]+>/g, "") ||
                "",
            }));
        this.movies.push(
            ...newMovies.filter(
            (m) =>
                !this.movies.find(
        (existing) => existing.id === m.id
                )
            )
        );
        });
    },
    removeMovie(id) {
    this.movies = this.movies.filter(
        (m) => m.id !== id
    );
    },
},
mounted() {
    this.fetchInitialMovies();
},
};
</script>

<style scoped>
.container {
padding: 60px 0;
background-color: #211e1e;
color: #fff;
width: 100%;
}

.header-section {
display: flex;
justify-content: space-between;
align-items: center;
margin: 0 10% 30px 10%;
padding: 0;
}

h2 {
margin: 0;
font-size: 2rem;
font-weight: 400;
color: #fff;
}

.search-container {
position: relative;
display: flex;
align-items: center;
}

.search-icon {
position: absolute;
left: 15px;
color: #888;
z-index: 1;
}

.search-box {
width: 300px;
padding: 12px 20px 12px 45px;
font-size: 1rem;
border-radius: 6px;
border: 1px solid #444;
background-color: #111;
color: white;
}

.search-box::placeholder {
color: #888;
}

.divider {
border: none;
height: 2px;
background: linear-gradient(90deg, #f3eee5, #f0ebe7);
margin: 0 10% 40px 10%;
border-radius: 1px;
}

.movie-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 40px;
margin: 0 10%;
padding: 0;
}

.movie-card {
background-color: #000;
border-radius: 8px;
overflow: hidden;
position: relative;
transition: transform 0.3s ease;
}

.movie-card:hover {
transform: translateY(-5px);
}

.image-wrapper {
position: relative;
width: 100%;
height: 400px;
overflow: hidden;
}

.image-wrapper img {
width: 100%;
height: 100%;
object-fit: cover;
display: block;
}

.close-btn {
position: absolute;
top: 15px;
right: 15px;
background-color: rgba(0, 0, 0, 0.7);
border: none;
color: white;
font-size: 20px;
font-weight: bold;
width: 32px;
height: 32px;
text-align: center;
line-height: 32px;
border-radius: 4px;
cursor: pointer;
transition: background-color 0.3s;
}

.close-btn:hover {
background-color: #e74c3c;
}

.card-content {
background-color: #3f3f3f;
padding: 20px;
min-height: 140px;
}

.card-content h3 {
margin: 0 0 10px 0;
font-size: 1.3rem;
font-weight: 600;
color: #fff;
}

.card-content p {
margin: 0;
font-size: 0.95rem;
color: #aaa;
line-height: 1.5;
display: -webkit-box;
-webkit-line-clamp: 4;
-webkit-box-orient: vertical;
overflow: hidden;
}

@media (max-width: 768px) {
.container {
    padding: 40px 15px;
}

.header-section {
    padding: 0 10px;
}

.movie-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 25px;
    padding: 0 10px;
}

.header-section {
    flex-direction: column;
    gap: 20px;
    align-items: stretch;
}

.search-box {
    width: 100%;
}
}

@media (max-width: 480px) {
.movie-grid {
    grid-template-columns: 1fr;
    gap: 20px;
}
}
</style>
