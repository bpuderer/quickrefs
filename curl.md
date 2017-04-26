Option|Description
---|---
--connect-timeout <seconds>|Number of seconds connection is allowed to take
-d, --data <data>|Sends specified <data> in POST with content-type application/x-www-form-urlencoded. If data starts with "@" then it reads from file. ASCII.  For binary, use --data-binary
-H, --header <header>|Add header
-i, --include|Display response headers
-m, --max-time <seconds>|Number of seconds whole operation is allowed to take
-o, --output <file>|Write output to file instead of stdout
-X, --request <command>|HTTP request method. Usually not needed since options specify method. Commonly used for DELETE and PUT
-s, --silent|Silent mode
--trace-time|Add timestamps to trace/verbose log lines
--trace <file>|Full trace dump. Use "-" as file to send to stdout
--trace-ascii <file>|Full trace dump, ascii only. Use "-" as file to send to stdout
-v, --verbose|Verbose output
-w, --write-out <format>|Write output to stdout according to format. See man page for list of variables. Ex. curl -s -o /dev/null -w "%{http_code}\n" http://localhost:1234/api/v1/test

Method|Example
---|---
GET|curl -i http://localhost:1234/books
OPTIONS|curl -i -X OPTIONS http://localhost:1234/books
HEAD|curl -i --head http://localhost:1234/books
DELETE|curl -i -X DELETE http://localhost:1234/books
PUT|curl -i -X PUT -H "Content-Type: application/json" -d @example.json http://localhost:1234/books
POST|curl -i -H "Content-Type: application/json" -d '{"identifier": {"ISBN-10": "0374530637"}, "title": "Wise Blood"}' http://localhost:1234/books


[curl man page](https://curl.haxx.se/docs/manpage.html)

[curl on github](https://github.com/curl/curl)
