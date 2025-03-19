# MODULE 6

# REFLECTION NOTES - COMMIT 1
I implemented the handle_connection function to manage incoming HTTP requests. The function reads and processes request lines from a TcpStream, stopping when an empty line is encountered. Running the program and accessing it from the browser confirms that the server correctly receives and logs the request headers.