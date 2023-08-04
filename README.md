<!DOCTYPE html>
<html>
<head>
    <title>Blog Creator</title>
    <style>

body {
    font-family: Arial, sans-serif;
    margin: 20px;
}

h1 {
    text-align: center;
}

div {
    margin-bottom: 10px;
}

label {
    display: block;
    font-weight: bold;
}

input[type="text"],
textarea,
input[type="file"] {
    width: 100%;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    display: block;
    padding: 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #0056b3;
}

#blogEntries {
    margin-top: 20px;
}

h2 {
    margin-bottom: 5px;
}

p {
    margin-top: 5px;
}

img {
    max-width: 100%;
    margin-top: 10px;
}

iframe {
    width: 100%;
    height: 315px;
    margin-top: 10px;
}
    </style>
    <!-- Add any CSS or external libraries here -->
</head>
<body>
    <h1>Create Your Blog</h1>
    <div>
        <label for="blogTitle">Blog Title:</label>
        <input type="text" id="blogTitle" />
    </div>
    <div>
        <label for="blogContent">Blog Content:</label>
        <textarea id="blogContent"></textarea>
    </div>
    <div>
        <label for="blogImage">Upload Image:</label>
        <input type="file" id="blogImage" accept="image/*" />
    </div>
    <div>
        <label for="blogVideo">Add Video URL:</label>
        <input type="text" id="blogVideo" />
    </div>
    <button id="addBlogEntry">Add Blog Entry</button>
    <div id="blogEntries">
        <!-- Blog entries will be dynamically added here -->
    </div>

    <script>
        // Function to add a new blog entry
        function addBlogEntry() {
            const blogTitle = document.getElementById('blogTitle').value;
            const blogContent = document.getElementById('blogContent').value;
            const blogImage = document.getElementById('blogImage').files[0];
            const blogVideo = document.getElementById('blogVideo').value;
    
            // Create a new blog entry element
            const blogEntry = document.createElement('div');
            blogEntry.innerHTML = `
                <h2>${blogTitle}</h2>
                <p>${blogContent}</p>
                ${blogImage ? `<img src="${URL.createObjectURL(blogImage)}" alt="Blog Image" />` : ''}
                ${blogVideo ? `<iframe width="560" height="315" src="${blogVideo}" frameborder="0" allowfullscreen></iframe>` : ''}
            `;
    
            // Add the blog entry to the blogEntries div
            const blogEntries = document.getElementById('blogEntries');
            blogEntries.appendChild(blogEntry);
    
            // Clear input fields after adding the entry
            document.getElementById('blogTitle').value = '';
            document.getElementById('blogContent').value = '';
            document.getElementById('blogImage').value = '';
            document.getElementById('blogVideo').value = '';
        }
    
        // Add event listener to the "Add Blog Entry" button
        document.getElementById('addBlogEntry').addEventListener('click', addBlogEntry);
    </script>
</body>
</html>
