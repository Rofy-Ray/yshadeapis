🏁 Quick Start
==============

Don't worry. We get it! It's always more fun to jump right in and then read the documentation if something breaks. We got you covered.

> **Good to know:** Our current API is the Skin Shade Detection API. The Beauty & Fashion Product Recommendation API is also coming soon!

Get your API Key
----------------

Your API requests are authenticated using API keys. Any request that doesn't include an API key will return an error.

The best way to interact with our APIs is to use standard HTTP verbs as our APIs are organized around REST.

Before you start using the `skinshade` or `lips` endpoint, you need to generate an API key. This can be done by making a **GET** request to the `generatekey` endpoint. This endpoint is rate-limited to 1 request per month for the free tier.

Here is an example of how to make a request to the `generatekey` endpoint using curl:

`curl --location 'https://api.robomua.com/api/generatekey'`

The response will be a JSON object containing your API key:

`{
  "roboKey": "your-api-key"
}`

> **Good to know:** To authenticate your API request, you will need to include the API key in the request header as follows:
>
> `x-api-key`: <API_KEY>
>
> Be sure to replace <API_KEY> with your actual API key.

Make your first request
-----------------------

Send an authenticated request to our endpoints to make your first request.

-   The `skinshade` endpoint will fetch the exact skin shade of the person from the image file based on the user's skin tone and undertones.
-   The `lips` endpoint will return the processed image with the lipstick color applied to the lips.
-   The `hairswap` endpoint returns a processed image with the newly selected hairstyle.

Once you have your API key, you can start using the endpoints.

All endpoints accept **POST** requests with an image file in the request body. The `lips` endpoint also requires the name of a color and the `hairswap` endpoint also requires a number corresponding to the preferred hairstyle.

The image file should be png, jpg, jpeg, or heic.

### Skinshade Endpoint

Here is an example of how to make a request to the `skinshade` endpoint using curl:

`curl --location 'https://api.robomua.com/api/skinshade'\
--header 'x-api-key: your-api-key'\
--form 'file=@"/path/to/your/image.jpeg"'`

The response will be a JSON object containing the detected skin shade and tone range:

`{
  "skinShade": "#hex-color",
  "toneRange": "tone-range"
}`

### Lips Endpoint

Take a look at how you can use the `lips` endpoint via curl:

`curl --location 'https://api.robomua.com/api/lips'\
--header 'x-api-key: your-api-key'\
--form 'file=@"/path/to/your/image.jpeg"'\
--form 'color="color-name"'`

The response will be a JSON object containing a base64 string of the binary data of the image with the lipstick color applied:

`{
  "lipsImage": "base64-encoded-string"
}`

### Hairswap Endpoint

Here is how you can send a request to the `hairswap` endpoint via curl:

`curl --location 'api.robomua.com/api/hairswap'\
--header 'x-api-key: your-api-key'\
--form 'file=@"/path/to/your/image.jpeg""'\
--form 'hair="integer-for-style"'`

You will get a JSON object response containing a base64 string of the binary data of the image with the new hairstyle:

`{
  "hairstyleImage": "base64-encoded-string"
}`