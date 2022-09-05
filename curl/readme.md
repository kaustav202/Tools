# curl 

cURL is a command-line utility and a library for accessing remote resources, communicating with servers and transfering data over the network. It supports a range of protocols including HTTP, FTP, IMAP, LDAP, POP3, SMTP.

The most common use cases for curl are:

- Downloading files from the internet
- Endpoint testing
- Debugging
- Error logging
- Scripting
- Forensic analysis

</br>

### Get a response from a server

Everything from server is a response to the request. So getting a HTML page is same as downloading a file.This retrieves the content from the specified URL and prints it to the terminal.

`curl http://info.cern.ch/`

</br>

Download a file ( say Google logo ).

`curl https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png`

</br>

### Save the file with a default file name

</br>

Every file that is served on the internet has a filename. To use the same filename as the downloaded filename use -O flag.


`curl -O http://www.google.com/robots.txt`

</br>

Save the file with custom name

`curl -o http://www.google.com/robots.txt googleRobots.txt`

</br>

### Download multiple files

To download multiple files, separate them with a white space.

`curl url1 url2 url3`

</br>

### Resume Downloading

</br>

If you have already partially transferred a file, you can resume the transfer by using the -C flag. Optionally, offset from which transfer needs to be continued could be passed as a parameter to the -C flag.

`curl -C 1024 http://seeni.linuxhandbook.org/files/largeFile.mpv -O`

</br>

### Following Redirects

</br>

The -L option should be used if you wish cURL to follow redirects.

`curl -L http://www.instagram.com/`

</br>

6 View Request Headers and Connection Information

</br>

We saw how to use cURL to inspect HTTP response headers in the previous section. However, you may wish to see more information about a request, such as the request headers sent and the connection procedure, on occasion. For this, cURL provides the -v flag (sometimes known as "verbose mode"), which can be used as follows:

`curl -v https://www.atatus.com/`

Request data, response headers, and other information about the request, such as the IP used and the SSL handshake process, are all included in the output.

</br>

### Upload a file

</br>

To upload a file to the server, one needs to use -T flag followed by the file path on your local system.

`curl -T uploadFile.txt http://upload.linuxhandbook.org/files`

</br>


### Delete a file

</br>

To delete a file named deleteFile.txt in a server, one can use -X flag which is intended for any HTTP verb/method(like GET, POST, PUT, DELETE, PATCH). Most of the FTP servers will have configured DELETE method if not all advanced HTTP methods.

`curl -X DELETE http://upload.linuxhandbook.org/files/deleteFile.txt`

</br>

### Authentication

</br>

When the server is configured to serve for only certain individuals with credentials, they will be provided with username and password. One can make login with the help of -u flag.

`curl -u username:password http://seeni.linuxhandbook.org/files/tasks.txt`

</br>

### Ignore SSL certificates

</br>

If you trust the sources and you want to do a data transfer, you can ignore SSL certificate validation by using -k flag.

`curl -k https://notSoSecure.org/files/logoDetails.tgz`

</br>

### Get Header Information also

</br>

To display the header information along with transferred data, use the -i flag.

`curl -i http://www.google.com/robots.txt`

</br>

### Change User Agent

</br>

Some websites and servers don’t allow certain kinds of devices to access their systems. But how do they know that we are using a specific kind of device? This is due to the User-Agent HTTP header field. We can change this User Agent with -A flag.

`curl -A "Mozilla FireFox(42.0)" http://notAllowedForCLI.sites.org/randomFile.png`

</br>

### Setting HTTP Request Headers

</br>

You may need to set special headers on HTTP requests while testing APIs. The -H option in cURL can be used for this purpose. You should run the following command to transmit the custom header X-My-Custom-Header with the value 123 to https://httpbin.org/get:

`curl -H 'X-My-Custom-Header: 123' https://httpbin.org/ge`

`curl -H 'User-Agent: Mozilla/5.0' -H 'Host: www.instagram.com' https://www.instagram.com/`

</br>

### Make POST Requests

</br>

cURL sends GET requests by default, but you can use the -d or --data options to send POST requests. The ampersand (&) character must be used to separate all of the fields as key=value pairs. Make a POST request to httpbin.org with the following arguments, for example:

`curl --data "firstname=atatus" https://httpbin.org/post`

Any special characters in the value, such as @, %, =, or spaces, should be manually URL-encoded. So, if you wanted to enter the value "test@example.com" for the argument "email," you'd use:

`curl --data-urlencode "email=test@example.com" --data-urlencode "name=atatus" https://httpbin.org/post`

Sending data saved on a file:

`curl --data @params.txt example.com`

Directly send json data by informing in header:

`curl --data '{"email":"test@example.com", "name": ["atatus"]}' -H 'Content-Type: application/json' https://httpbin.org/post`

</br>


### Sending data to the Server

</br>

If the server needs some data such as token or API key, use -d flag to send the data. Data that needs to be sent should follow the flag in the command. One can use “&” to combine multiple data. This is usually done by GET and POST requests in browsers. This is one of the ways by which you can send your form information.

`curl -d "token=34343abvfgh&name='seeni'" http://api.restful.org/getcontent`

</br>

### Write Cookies to a File

</br>

Cookies are some small information that allows maintaining a session with a stateless HTTP protocol. If you want to know more about Cookies, refer to this great resource.

To write cookies to a file, -c flag followed by the cookie filename should be used.

`curl -c googleCookie.txt http://www.google.com/files`

</br>


### Reading Cookies from a File

</br>

To read a cookie from the file, -b flag followed by cookie filename can be used.

`curl -b googleCookie.txt http://www.google.com/files`

Note that -b flag only reads the cookie from the file. So if the server resends another cookie, you might need to use -c option to write them.

</br>

### Start a new Session

</br>

If you want to initiate a new session by discarding the cookies, use -j flag. It starts a new session even if you have provided the cookie file to read with -b flag.

`curl -b googleCookie.txt http://www.google.com/files -j`

</br>

### cURL's --resolve Flag

</br>

The --resolve flag can be used to avoid the problem outlined above. The resolve flag will deliver the request to the port and IP of your choice, while appropriately sending the website name over SSL/TLS and HTTP.

Consider the preceding scenario. You can use the following syntax to send HTTPS to the local server 192.168.0.1:

`curl https://sample1.com/ --resolve sample1.com:192.168.0.1:443`
