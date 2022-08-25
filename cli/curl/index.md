**curl cheat**
===

## Perform an HTTP GET request
When you perform a request, curl will return the body of the response:
```shell
curl https://devcheat.github.io/
```
## Get the HTTP response headers
By default the response headers are hidden in the output of curl. To show them, use the i option:
```shell
curl -i https://devcheat.github.io/
```
## Only get the HTTP response headers
Using the I option, you can get only the headers, and not the response body:
```shell
curl -I https://devcheat.github.io/
```
## Perform an HTTP POST request
The X option lets you change the HTTP method used. By default, GET is used, and it’s the same as writing
```shell
curl -X GET https://devcheat.github.io/
```
## Using -X POST will perform a POST request.

You can perform a POST request passing data URL encoded:
```shell
curl -d "option=value&something=anothervalue" -X POST https://devcheat.github.io/
```
In this case, the `application/x-www-form-urlencoded` `Content-Type` is sent.

## Perform an HTTP POST request sending JSON
Instead of posting data URL-encoded, like in the example above, you might want to send JSON.

In this case you need to explicitly set the Content-Type header, by using the H option:
```shell
curl -d '{"option": "value", "something": "anothervalue"}' -H "Content-Type: application/json" -X POST https://devcheat.github.io/
```
## You can also send a JSON file from your disk:
```shell
curl -d "@my-file.json" -X POST https://devcheat.github.io/
```
## Perform an HTTP PUT request
The concept is the same as for POST requests, just change the HTTP method using `-X PUT`

## Follow a redirect
A redirect response like 301, which specifies the Location response header, can be automatically followed by specifying the L option:
```shell
curl https://devcheat.github.io/
```
will not follow automatically to the HTTPS version which I set up to redirect to, but this will:
```shell
curl -L https://devcheat.github.io/
```
## Store the response to a file
Using the o option you can tell curl to save the response to a file:
```shell
curl -o file.html https://devcheat.github.io/
```
You can also just save a file by its name on the server, using the O option:
```shell
curl -O https://devcheat.github.io/index.html
```
## Using HTTP authentication
If a resource requires Basic HTTP Authentication, you can use the u option to pass the `user:password` values:
```shell
curl -u user:pass https://devcheat.github.io/
```
## Set a different User Agent
The user agent tells the server which client is performing the request. By default curl sends the curl/<version> user agent, like: `curl/7.54.0`.

You can specify a different user agent using the --user-agent option:
```shell
curl --user-agent "my-user-agent" https://flaviocopes.com
```
## Inspecting all the details of the request and the response
Use the `--verbose` option to make curl output all the details of the request, and the response:
```shell
curl --verbose -I https://devcheat.github.io/
```

----
