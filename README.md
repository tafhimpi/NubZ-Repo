# Tafhim

Personal website of Tafhim. Plain HTML, CSS and JavaScript, plus one serverless function for the live Spotify "Now playing" card.

## Structure

- `index.html` is the whole site.
- `api/now-playing.js` is a Vercel serverless function that reads the current Spotify track.
- `.env.example` lists the environment variables the function needs.

## Deploy

1. Push this repository to GitHub.
2. Import it at [vercel.com/new](https://vercel.com/new) and click **Deploy**.
3. Add the domain under **Settings > Domains**.

## Live Spotify "Now playing" setup

1. Open the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard) and create an app. Set the redirect URI to `https://example.com/callback` and tick **Web API**.
2. Copy the **Client ID** and **Client Secret**.
3. Open this URL in your browser (replace `CLIENT_ID`), log in and accept:

   ```
   https://accounts.spotify.com/authorize?client_id=CLIENT_ID&response_type=code&redirect_uri=https%3A%2F%2Fexample.com%2Fcallback&scope=user-read-currently-playing%20user-read-recently-played
   ```

4. You land on `example.com/callback?code=XXXX`. Copy the value after `code=`.
5. Exchange it for a refresh token (on Windows use `curl.exe`):

   ```
   curl.exe -X POST https://accounts.spotify.com/api/token -u CLIENT_ID:CLIENT_SECRET -d grant_type=authorization_code -d code=XXXX -d redirect_uri=https://example.com/callback
   ```

6. Copy `refresh_token` from the response.
7. In Vercel add `SPOTIFY_CLIENT_ID`, `SPOTIFY_CLIENT_SECRET` and `SPOTIFY_REFRESH_TOKEN` under **Settings > Environment Variables**, then **Redeploy**.
