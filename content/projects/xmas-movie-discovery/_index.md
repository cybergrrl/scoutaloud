+++
title = "Xmas Movie Discovery"
template = "xmas-movies-homepage.html"
paginate_by = 50
paginate_path = "page"
+++

<div class="movie-grid">
  {% for movie in movies %}
    <div class="movie-card">
      <img src="https://image.tmdb.org/t/p/w342/{{ movie.TMDB_ID }}.jpg" alt="{{ movie.Film_title }}">
      <h3>{{ movie.Film_title }}</h3>
    </div>
  {% endfor %}
</div>