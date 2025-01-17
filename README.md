# Node.js HTTP Server Hanging Response Bug

This repository demonstrates a common bug in Node.js HTTP servers: forgetting to end the response.  This can cause clients to hang indefinitely, waiting for a response that never comes.

## Bug
The `bug.js` file contains the problematic code.  The server sends a response but fails to call `res.end()`. This omission prevents the server from closing the connection, resulting in a hanging response.

## Solution
The `bugSolution.js` file demonstrates the correct way to handle the response. The `res.end()` method is called to signal the end of the response, ensuring that the client receives the complete response and the connection is closed properly.

## How to Reproduce
1. Clone this repository.
2. Navigate to the repository's directory in your terminal.
3. Run `node bug.js`.
4. Make a request to `http://localhost:3000` using a tool like `curl` or your browser.  You'll likely observe that the request hangs.
5. Repeat steps 3 and 4 with `node bugSolution.js`.  This time the request should complete successfully.