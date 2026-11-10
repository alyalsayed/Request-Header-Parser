# Request Header Parser Microservice

A small Express.js API that parses request metadata from the client and returns it as JSON. This project is part of the freeCodeCamp Back End Development and APIs curriculum and demonstrates how to read browser/request headers in a Node.js application.

## Features

- Returns the client's IP address
- Returns the preferred language from the `Accept-Language` header
- Returns the browser/software details from the `User-Agent` header
- Built with Express.js and CORS support

## API endpoint

### GET /api/whoami

Returns a JSON object containing the request metadata.

Example response:

```json
{
  "ipaddress": "::ffff:127.0.0.1",
  "language": "en-US,en;q=0.9",
  "software": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/124.0.0.0 Safari/537.36"
}
```

## Local development

### Prerequisites

- Node.js
- npm

### Installation

```bash
npm install
```

### Run the application

```bash
npm start
```

The app listens on the port defined by `PORT`, or defaults to `3000` when not set.

```bash
PORT=3000 npm start
```

Then open:

```text
http://localhost:3000
```

## Project structure

```text
.
├── index.js          # Express server and API route logic
├── public/           # Static frontend assets
├── views/            # HTML view served by the app
├── package.json      # Project metadata and scripts
├── package-lock.json # Dependency lock file
├── README.md         # Documentation
├── .env.example      # Optional environment configuration (if present)
└── submit.PNG        # Project submission image
```

## Implementation notes

The main route is:

```js
app.get("/api/whoami", function (req, res) {
  const ipaddress = req.ip;
  const language = req.headers["accept-language"];
  const software = req.headers["user-agent"];

  res.json({
    ipaddress,
    language,
    software,
  });
});
```

This uses Express request metadata to extract the client request information and send it back in JSON format.

## Testing

The project is expected to satisfy the following requirements:

- A request to `/api/whoami` returns the client IP address in the `ipaddress` field.
- A request to `/api/whoami` returns the preferred language in the `language` field.
- A request to `/api/whoami` returns the software/browser information in the `software` field.

## License

This project is distributed under the MIT license, as specified in the package metadata.

## Related

- freeCodeCamp Back End Development and APIs
- Request Header Parser Microservice challenge
