---
layout: page
title: Books
permalink: /books/
---

<style>
/* Grid Container */
.bookshelf-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Responsive columns */
    gap: 2rem; /* Consistent spacing between books */
    margin-bottom: 3rem;
}

/* Individual Book Item */
.book-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
}

/* Cover Image Container (enforces uniform height) */
.book-cover-container {
    width: 100%;
    height: 220px; /* Maximum height for all covers */
    display: flex;
    justify-content: center;
    align-items: flex-end; /* Aligns covers along the bottom edge */
    margin-bottom: 0.75rem;
}

/* The actual image */
.book-cover {
    max-height: 100%;
    max-width: 100%;
    box-shadow: 0 4px 6px rgba(0,0,0,0.3); /* Adds a subtle depth */
    border-radius: 2px;
}

/* Text elements */
.book-title {
    font-size: 0.95rem;
    font-weight: bold;
    line-height: 1.2;
    margin-bottom: 0.25rem;
    color: #333; /* Use your site's text color */
}

.book-author {
    font-size: 0.8rem;
    color: #666; /* Use your site's lighter text color */
    font-style: italic;
}

/* Category header */
h3.bookshelf-category {
    border-bottom: 2px solid #eee;
    padding-bottom: 0.5rem;
    margin-top: 2rem;
    margin-bottom: 1.5rem;
}
</style>

## Bookshelf

I am an avid reader, focusing primarily on psychology, human behavior, and high-performance habits. Here is a curated collection of books I've explored:

{% for section in site.data.books %}
  <h3 class="bookshelf-category">{{ section.category }}</h3>
  <div class="bookshelf-grid">
    {% for book in section.books %}
      <div class="book-item">
        <div class="book-cover-container">
          <img src="../images/books/{{ book.image }}" alt="{{ book.title }} cover" class="book-cover">
        </div>
        <div class="book-title">{{ book.title }}</div>
        <div class="book-author">{{ book.author }}</div>
      </div>
    {% endfor %}
  </div>
{% endfor %}

---
