# MODULE 6

# REFLECTION NOTES - COMMIT 1
I implemented the handle_connection function to manage incoming HTTP requests. The function reads and processes request lines from a TcpStream, stopping when an empty line is encountered. Running the program and accessing it from the browser confirms that the server correctly receives and logs the request headers.

# REFLECTION NOTES - COMMIT 2
![Commit 2 screen capture](/assets/images/commit2.png)

I updated the handle_connection function to return a simple HTML page to the browser. This implementation involves reading the hello.html file and sending it as an HTTP response with the appropriate headers. By adding the Content-Length header, the browser can properly interpret the content length. 