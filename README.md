# MODULE 6

# REFLECTION NOTES - COMMIT 1
In this commit, I implemented the handle_connection function to manage incoming HTTP requests. The function reads and processes request lines from a TcpStream, stopping when an empty line is encountered, which signifies the end of the HTTP request headers. This approach allows the server to correctly extract and store request data for further processing.

To verify its functionality, I ran the program and accessed the server from a browser. The console output displayed the parsed request headers, confirming that the server successfully captured details such as the HTTP method, requested path, and various header fields. This implementation lays the foundation for further enhancements, such as serving dynamic responses based on request content.

# REFLECTION NOTES - COMMIT 2
![Commit 2 screen capture](/assets/images/commit2.png)

In this commit, I enhanced the handle_connection function to generate and return a simple HTML page to the browser. Previously, the server only logged incoming requests without responding meaningfully. Now, by reading the hello.html file and serving it as an HTTP response, the server can properly interact with web clients.

To ensure correct rendering, I included the Content-Length header in the response, allowing the browser to determine the size of the incoming content. This change is essential for maintaining proper HTTP communication, ensuring that clients can load the page without issues. Testing the implementation by accessing the server in a browser confirmed that the page loads correctly.

# REFLECTION NOTES - COMMIT 3
![Commit 3 screen capture](/assets/images/commit3.png)

Here, I improved the handle_connection function by introducing request validation and selective responses. Previously, the server always returned hello.html regardless of the request, but now it properly checks the requested path and returns the appropriate response.

The key change was extracting the first request line and checking if it matches "GET / HTTP/1.1". If the request is valid, the server responds with hello.html; otherwise, it returns a 404.html page with a "404 Not Found" status. This change ensures that the server can handle unknown paths in a better way instead of always displaying the same content.

Through this implementation, I gained a deeper understanding of handling HTTP requests dynamically in Rust. It is important to correctly parse the request and structure the response headers to follow proper HTTP standards. I also learned the importance of sending the correct status codes and content types, which are essential for web development.

# REFLECTION NOTES - COMMIT 4

In this milestone, I simulated a slow response by adding a 10-second delay when accessing the /sleep endpoint. While handling this request, the server pauses execution, causing the response to be delayed. However, the server still processes other requests before the delay if they arrive first. This demonstrates a key limitation of single-threaded servers—requests are handled sequentially, and long-running tasks can slow down subsequent ones. To improve performance, multithreading is needed to handle multiple requests in parallel. Implementing this will enhance user experience by making it smoother.

# REFLECTION NOTES - COMMIT 5
In this milestone, I improved the web server by implementing a ThreadPool to handle multiple requests concurrently. Previously, the server was single-threaded, meaning it could only process one request at a time. If a request took too long, such as with the /sleep endpoint, all other incoming requests would be blocked until the current one finished.

By introducing a ThreadPool, the server can now create a pool of worker threads that execute requests in parallel instead of sequentially. When a request arrives, it is assigned to an available worker thread, preventing long-running requests from delaying others. This significantly improves performance, especially when handling multiple users simultaneously.

# REFLECTION NOTES - BONUS
In this bonus commit, I refactored the new function by renaming it to build, enhancing clarity and readability. The original function name, new, while functional, was somewhat generic and did not clearly convey its purpose. The new name, build, makes it more intuitive that this function is responsible for constructing a ThreadPool instance from scratch. Alongside this change, I updated its usage in main.rs to ensure consistency across the codebase.

This small yet meaningful adjustment improves both code maintainability and readability, making it easier for future contributors to understand its role at a glance. This reinforced the importance of thoughtful naming conventions, as they play a crucial role in writing clean and maintainable code. This adjustment also ensures that the code remains intuitive and easy to work with as the project evolves.