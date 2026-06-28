# Curl?

cURL, which stands for client URL and can be written as curl (which I’ll do for the remainder of the blog because I’m lazy). Open the Terminal - I like to do this with: `Command+Space` then typing `Terminal`

## Do you have cURL?

If you are running OS X that isn’t 10 years old, you probably have curl already installed. You can pull up the “man pages” or manual by doing the command below in the terminal :

```
curl --manual
```

## How to write

To write a curl statement, start with the word `curl`, followed by any required configuration flags (options), and end with the target URL. By default, running curl with just a URL executes a basic HTTP `GET` request.

### Essential Flags

- `-X`: Specifies the HTTP request method (e.g., `GET`, `POST`, `PUT`, `DELETE`).
- `-H`: Adds custom HTTP headers, such as content types or authorization tokens.
- `-d`: Sends specified data in a request body (automatically triggers a `POST` request).
- `-o`: Saves the downloaded response directly to a local file instead of printing it to the terminal screen.
- `-I`: Fetches the HTTP response headers only.
- `-L`: Forces curl to follow server redirects
  Try running these commands. What do they do?

```bash
curl google.com
```

```bash
curl example.com
```

```bash
curl http://numbersapi.com/random/trivia
```

```bash
curl http://api.open-notify.org/astros.json
```

## GET and POST

JSONPlaceholder: A fake online REST API for testing fake blog posts and comments.Fetch fake data:

```bash
curl https://jsonplaceholder.typicode.com/posts
```

a post:

```bash
curl -X POST -H "Content-Type: application/json" -d '{"title": "SEA", "body": "alex-is-gonzalez", "userId": 1}' https://jsonplaceholder.typicode.com/posts
```

Now you try post your github handle !

# cURL is cool but what about Postman?

Yes, we can do this in the terminal but there a really nice GUI we can use instead. Head over to [postman](https://www.postman.com/downloads/) and download the desktop. This will probably be your best friend this week.

Ignore this, just saving it here so I don't lose the endpoint

https://pokeapi.co/api/v2/ability/?limit=20&offset=20
