---
layout: post
title: About
permalink: /about/
comments: true
---

## As a conversation Starter
-What I do for a living?
-Where I was born?
-What religon I am?

Here are the places I have lived.

<comment>
Flags are made using Wikipedia images
</comment>

<style>
    /* Style looks pretty compact, 
       - grid-container and grid-item are referenced the code 
    */
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Dynamic columns */
        gap: 10px;
    }
    .grid-item {
        text-align: center;
    }
    .grid-item img {
        width: 100%;
        height: 100px; /* Fixed height for uniformity */
        object-fit: contain; /* Ensure the image fits within the fixed height */
    }
    .grid-item p {
        margin: 5px 0; /* Add some margin for spacing */
    }

    .image-gallery {
        display: flex;
        flex-wrap: nowrap;
        overflow-x: auto;
        gap: 10px;
        }

    .image-gallery img {
        max-height: 150px;
        object-fit: cover;
        border-radius: 5px;
    }
</style>

<!-- This grid_container class is used by CSS styling and the id is used by JavaScript connection -->
<div class="grid-container" id="grid_container">
    <!-- content will be added here by JavaScript -->
</div>

<script>
    // 1. Make a connection to the HTML container defined in the HTML div
    var container = document.getElementById("grid_container"); // This container connects to the HTML div

    // 2. Define a JavaScript object for our http source and our data rows for the Living in the World grid
    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
        {"flag": "0/01/Flag_of_California.svg", "greeting": "Hey", "description": "California - forever years"}, ];

    // 3a. Consider how to update style count for size of container
    // The grid-template-columns has been defined as dynamic with auto-fill and minmax

    // 3b. Build grid items inside of our container for each row of data
    for (const location of living_in_the_world) {
        // Create a "div" with "class grid-item" for each row
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  // This class name connects the gridItem to the CSS style elements
        // Add "img" HTML tag for the flag
        var img = document.createElement("img");
        img.src = http_source + location.flag; // concatenate the source and flag
        img.alt = location.flag + " Flag"; // add alt text for accessibility

        // Add "p" HTML tag for the description
        var description = document.createElement("p");
        description.textContent = location.description; // extract the description

        // Add "p" HTML tag for the greeting
        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  // extract the greeting

        // Append img and p HTML tags to the grid item DIV
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);

        // Append the grid item DIV to the container DIV
        container.appendChild(gridItem);
    }
</script>

### Journey through Life

Here is what I did at those places

- 👼 Born in California but have Afghan blood
- 🏫 Was enrolled in to multiple elemetary schools but the only one I can remember is Magnolia elementary school in El Cajon(CA)
- 🏫 Went to Oak Valley Middle School 2021-2023
- ⚽ Joined a soccer team
- 🏢 Worked at my dad's store
- 🎓 Graduating in Del Norte High School 2028

### Culture, Family, Fun and some Photos of Me and My Family!!!

For me my faith and culture as well as the support of my family dictates my life

- I am 100% Afghan according to my Family tree
- My family consists of 2 parents 4 sibling 5 uncles 5 aunts 3 grandparents and soo many cousins I cant count
- I am a muslim

<img width="478" height="500" alt="Image" src="https://github.com/user-attachments/assets/408c3f8a-2bfa-47c4-8d13-afe54ebe07de" />
<img width="354" height="450" alt="Image" src="https://github.com/user-attachments/assets/2f245b1c-e2a9-4b8b-9702-f94fd8d78b0d" />
<img width="485" height="500" alt="Image" src="https://github.com/user-attachments/assets/ba251b73-362e-486c-a18c-bd1a63e44d3f" />
<img width="481" height="450" alt="Image" src="https://github.com/user-attachments/assets/50c6ae52-2da6-425f-b194-ea389764856a" />
