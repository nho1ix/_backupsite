---
title: "Business Ideas"
description: 'The fast-loading business ideas site with no ads.'
layout: single
---

## Ideas To Try to Make A Business Out Of

<div class="search js-only">
  <input type="text" id="search" placeholder="Search ideas...">
  <button id="clear-search">
    <svg xmlns="http://www.w3.org/2000/svg" class="ionicon" viewBox="0 0 512 512"><title>Backspace</title><path d="M135.19 390.14a28.79 28.79 0 0021.68 9.86h246.26A29 29 0 00432 371.13V140.87A29 29 0 00403.13 112H156.87a28.84 28.84 0 00-21.67 9.84v0L46.33 256l88.86 134.11z" fill="none" stroke="currentColor" stroke-linejoin="round" stroke-width="32"></path><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="32" d="M336.67 192.33L206.66 322.34M336.67 322.34L206.66 192.33M336.67 192.33L206.66 322.34M336.67 322.34L206.66 192.33"></path></svg>
  </button>
</div>

<script>
// @license magnet:?xt=urn:btih:5ac446d35272cc2e4e85e4325b146d0b7ca8f50c&dn=unlicense.txt Unlicense

document.addEventListener("DOMContentLoaded", () => {
  for (e of document.getElementsByClassName("js-only")) {
    e.classList.remove("js-only");
  }

  const business = document.querySelectorAll("#artlist li");
  const search = document.getElementById("search");
  const oldheading = document.getElementById("newest-ideas");
  const clearSearch = document.getElementById("clear-search");
  const artlist = document.getElementById("artlist");

  search.addEventListener("input", () => {
    // grab search input value
    const searchText = search.value.toLowerCase().trim().normalize('NFD').replace(/\p{Diacritic}/gu, "");
    const searchTerms = searchText.split(" ");
    const hasFilter = searchText.length > 0;

    artlist.classList.toggle("list-searched", hasFilter);
    oldheading.classList.toggle("hidden", hasFilter);

    // for each idea hide all but matched
    business.forEach(idea => {
      const searchString = `${idea.textContent} ${idea.dataset.tags}`.toLowerCase().normalize('NFD').replace(/\p{Diacritic}/gu, "");
      const isMatch = searchTerms.every(term => searchString.includes(term));

      idea.hidden = !isMatch;
      idea.classList.toggle("matched-idea", hasFilter && isMatch);
    })
  })

  clearSearch.addEventListener("click", () => {
    search.value = "";
    business.forEach(idea => {
      idea.hidden = false;
      idea.classList.remove("matched-idea");
    })

    artlist.classList.remove("list-searched");
    oldheading.classList.remove("hidden");
  })
})
// @license-end
</script>

## Newest Ideas

{{< artlist >}}

## Or Browse by Category...

{{< tagcloud >}}
