## Hi there 👋

<!--
**PinkCollarJobs/PinkCollarJobs** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Custom Search Engine</title>
</head>
<body>
    <h1>Search with Google Custom Search</h1>
    <input type="text" id="search-query" placeholder="Enter your search term">
    <button onclick="performSearch()">Search</button>

    <div id="search-results">
        <!-- Search results will be displayed here -->
    </div>

    <script>
<script>
    const API_KEY = 'AIzaSyDRi3Ahajy-jkonrLdmH6hDYZZ2Z-KIOC8'; // Replace with your actual API Key
    const CX = '326072ac378754cd0'; // Replace with your Custom Search Engine ID (CX)
    const predefinedQuery = 'customer_support_remote'; // Replace with the term you want to search automatically

    window.onload = function() {
        performSearch(predefinedQuery);
    };

    function performSearch(query) {
        const url = `https://www.googleapis.com/customsearch/v1?q=${encodeURIComponent(query)}&key=${API_KEY}&cx=${CX}`;

        fetch(url)
            .then(response => response.json())
            .then(data => {
                displayResults(data.items);
            })
            .catch(error => {
                console.error('Error fetching search results:', error);
                document.getElementById('search-results').innerHTML = 'Error loading results.';
            });
    }

    function displayResults(items) {
        if (!items || items.length === 0) {
            document.getElementById('search-results').innerHTML = 'No results found.';
            return;
        }

        let table = '<table border="1" style="width:100%;"><tr><th>Title</th><th>Link</th><th>Description</th></tr>';

        items.forEach(item => {
            table += `<tr>
                        <td>${item.title}</td>
                        <td><a href="${item.link}" target="_blank">${item.link}</a></td>
                        <td>${item.snippet}</td>
                      </tr>`;
        });

        table += '</table>';
        document.getElementById('search-results').innerHTML = table;
    }
</script>
    </script>
</body>
</html>
