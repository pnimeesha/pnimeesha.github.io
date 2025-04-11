---
layout: page
title: Search
permalink: /search/
---

<div id="search-container">
    <input type="text" id="search-input" placeholder="Search through the blog posts...">
    <ul id="results-container"></ul>
</div>

<script src="{{ site.baseurl }}/assets/simple-jekyll-search.min.js" type="text/javascript"></script>

<script>
    SimpleJekyllSearch({
    searchInput: document.getElementById('search-input'),
    resultsContainer: document.getElementById('results-container'),
    searchResultTemplate: '<div style="text-align: left !important;"><a href="{url}"><h1 style="text-align:left !important;">{title}</h1></a><span style="text-align:left !important;">{date}</span></div>',
    json: '{{ site.baseurl }}/search.json'
    });
</script>


<div>
 # Hi, These are the resources I have read or reading, Please feel free to let me know your recommendations.

## Books
- Design Patterns Book, <a href="https://refactoring.guru/design-patterns/book" target="_blank">Refactoring Guru</a>

#Interview Prep
- Chip Hyuen's [ML Interview book](https://huyenchip.com/ml-interviews-book)


## Interesting articles
# ML concepts
 - Simple and interesting explanation of PCA [Stack Overflow](https://stats.stackexchange.com/questions/2691/making-sense-of-principal-component-analysis-eigenvectors-eigenvalues/140579#140579)
                                                              
</div>
