# Working-with-External-Data
Before you read this i just want to say i couldnt get the error code to stop working so i can test my functions, i tried puttigg it in google and reading over the lesson and still had no clue, i dont know if the code works or not, maybe i missed something in the lecture about commenting out a part of it.



A dynamic, front-end web application that interfaces with The Cat API to browse cat breeds, view image carousels, and manage user favorites.

Features
Dynamic Breed Selection: Fetches and populates a dropdown with available cat breeds directly from the API.

Automated Image Carousel: Dynamically renders a Bootstrap-powered carousel displaying multiple images of the selected breed alongside detailed breed information.

Global Loading States: Utilizes Axios interceptors to globally manage cursor states and a visual progress bar during network requests.

Favorites Management: Allows users to toggle favorites on specific images (POST/DELETE) and view a curated carousel of their saved images.

Technology Stack
Core: HTML5, CSS3, JavaScript (ES6 Modules)

Libraries: Axios (via CDN) for network requests, Bootstrap 5 (via CDN) for UI components and carousel logic, jQuery (via CDN) for Bootstrap dependencies.

Installation & Setup
This project is designed to run directly in the browser without the need for a complex Node.js build pipeline or native C++ compilers.

Clone the repository to your local machine.

Open index.js and locate the API_KEY variable at the top of the file.

Replace the placeholder string with your personal access key from The Cat API.

Launch the project using a local development server (such as VS Code's Live Server extension) to avoid CORS restrictions.
Note: Do not open the file directly via the file:/// protocol, as the browser will block the module imports.

Technical Limitations & Trade-offs
To accurately assess this architecture, the following flaws and API quirks should be noted:

Progress Bar Inaccuracies: The Cat API does not consistently send a Content-Length header in its responses. The Axios onDownloadProgress event relies on this header to calculate the exact byte download percentage. A fallback has been implemented to force the bar to 100% upon completion, but true granular progress tracking is limited by the server's configuration.

Data Structure Inconsistencies: The data shape returned by the /images/search endpoint differs significantly from the /favourites endpoint. The logic must explicitly handle these shifting object shapes when building the UI, which creates a slight repetition in the DOM manipulation logic.

Global Dependency Injection: To bypass local build errors, Bootstrap and Axios are injected globally via CDN script tags in the HTML rather than bundled via npm. While this guarantees execution, it leaves the application vulnerable to external CDN outages.

Author
Carlos Rhymer
Software Engineer
