# ALX Project 0x14 — Reading API Documentation

## API Overview
TMDB (The Movie Database) API provides developers with access to a comprehensive, community-driven dataset including metadata for movies, TV shows, actors, images, ratings, and more. With an extensive set of endpoints, you can search, discover, and retrieve detailed information such as cast and crew, trailers, reviews, recommendations, and trending content. :contentReference[oaicite:1]{index=1}

## Version
### TMDB API Version: **v3** :contentReference[oaicite:2]{index=2}

## Available Endpoints
Here are some of the primary endpoints you can use:

- `/search/movie` – Search movies by keyword  
- `/movie/{movie_id}` – Get detailed movie data including synopsis, release date, runtime  
- `/movie/{movie_id}/credits` – Fetch cast and crew information  
- `/movie/{movie_id}/images` – Retrieve movie posters, backdrops, and stills  
- `/movie/popular` – List of current popular movies  
- `/movie/{movie_id}/reviews` – User reviews and ratings  
- `/movie/{movie_id}/recommendations` – Recommended movies based on a given movie  
- `/trending/movie/day` – Daily trending media  
- Authentication & account endpoints (token/session) – Login, get account state  
- Configuration endpoints – Static lists like languages, available images etc. :contentReference[oaicite:3]{index=3}

## Request and Response Format
Typical request (with API key in query):


#### Successful Response (example):
```json
{
  "id": 550,
  "title": "Fight Club",
  "overview": "A depressed man...",
  "release_date": "1999-10-15",
  "genres": [{ "id": 18, "name": "Drama" }],
  "runtime": 139,
  "vote_average": 8.4,
  "poster_path": "/bptfVGEQuv6vDTIMVCHjJ9Dz8PX.jpg"
}

{
  "cast": [
    { "cast_id": 4, "character": "Tyler Durden", "name": "Brad Pitt", "profile_path": "..."},
    ...
  ],
  "crew": [ /* crew info */ ]
}
``` :contentReference[oaicite:4]{index=4}

## Authentication
- Requests must include your **API key** as a query parameter: `api_key=YOUR_API_KEY`
- For account-specific methods (rating, account states), you must authenticate via temporary request token or session-based authentication.
- A bearer token may be required for some protected endpoints. :contentReference[oaicite:5]{index=5}

## Error Handling
Common HTTP error responses:
- **401 Unauthorized**: Invalid or missing API key
- **404 Not Found**: Resource not found
- **429 Too Many Requests**: Rate limited by API
- **400 Bad Request**: Parameter validation failure

Error response format example:
```json
{
  "status_code": 7,
  "status_message": "Invalid API key: You must be granted a valid key.",
  "success": false
}
``` :contentReference[oaicite:6]{index=6}

## Usage Limits and Best Practices
- TMDB API is free for non-commercial use, provided that you attribute TMDB in your application (e.g. in About or Credits). :contentReference[oaicite:7]{index=7}
- Rate limits are enforced—handle **429** responses by retrying with exponential backoff or caching responses.
- Only fetch the fields you actually need to reduce payload size.
- Use proper error and edge-case handling: fallback UI for no results, loading states, and retries.
- Respect pagination for endpoints such as search, reviews, or trending.

---

Let me know if you’d like me to also generate the `constants` file or TypeScript types for integrating this API into your Next.js app!
::contentReference[oaicite:8]{index=8}
