# MODULE 6

# REFLECTION NOTES - COMMIT 1
I implemented the handle_connection function to manage incoming HTTP requests. The function reads and processes request lines from a TcpStream, stopping when an empty line is encountered. Running the program and accessing it from the browser confirms that the server correctly receives and logs the request headers.

# REFLECTION NOTES - COMMIT 2
![Commit 2 screen capture](/assets/images/commit2.png)

I updated the handle_connection function to return a simple HTML page to the browser. This implementation involves reading the hello.html file and sending it as an HTTP response with the appropriate headers. By adding the Content-Length header, the browser can properly interpret the content length. 

# REFLECTION NOTES - COMMIT 3
![Commit 3 screen capture](/assets/images/commit3.png)

Here, I improved the handle_connection function by introducing request validation and selective responses. Previously, the server always returned hello.html regardless of the request, but now it properly checks the requested path and returns the appropriate response.

The key change was extracting the first request line and checking if it matches "GET / HTTP/1.1". If the request is valid, the server responds with hello.html; otherwise, it returns a 404.html page with a "404 Not Found" status. This change ensures that the server can handle unknown paths in a better way instead of always displaying the same content.

Through this implementation, I gained a deeper understanding of handling HTTP requests dynamically in Rust. It is important to correctly parse the request and structure the response headers to follow proper HTTP standards. I also learned the importance of sending the correct status codes and content types, which are essential for web development.