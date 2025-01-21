# ALX Project 0x14

## API Overview
The MoviesDatabase API is a powerful tool for accessing data about movies, TV shows, and actors. It offers a wide range of features, including:
- Searching for movies, TV shows, and people by name or keywords.
- Retrieving detailed information about specific movies or shows, such as cast, crew, trailers, and images.
- Accessing trending and popular content over different time periods.
- Managing user-specific watchlists, favorites, and ratings (with authentication).
- Filtering and discovering content based on genres, release dates, and more.

## Version
The current version of the MoviesDatabase API is **v3**, as stated in the official documentation.

## Available Endpoints
Below is a list of the main endpoints available in the MoviesDatabase API:

- **/movie/{movie_id}**: Fetch detailed information about a specific movie.
- **/tv/{tv_id}**: Retrieve details about a specific TV show.
- **/person/{person_id}**: Access information about an actor, director, or crew member.
- **/search/movie**: Search for movies based on a query string.
- **/search/tv**: Search for TV shows by name.
- **/search/person**: Look up actors, directors, or other crew members by name.
- **/genre/movie/list**: Get a list of available movie genres.
- **/trending/{media_type}/{time_window}**: Retrieve trending movies, TV shows, or people over a daily or weekly timeframe.
- **/discover/movie**: Discover movies by applying filters like genre, release date, and popularity.
- **/discover/tv**: Discover TV shows with similar filtering options.

## Request and Response Format
### Request Structure
A typical API request is structured as follows:
```
GET https://api.themoviedb.org/3/{endpoint}
```
#### Example Request
```
GET https://api.themoviedb.org/3/movie/550?api_key=YOUR_API_KEY
```

### Response Format
Responses are returned in JSON format. Here is an example response for a movie details request:
```json
{
  "id": 550,
  "title": "Fight Club",
  "overview": "An insomniac office worker...",
  "release_date": "1999-10-15",
  "genres": [
    { "id": 18, "name": "Drama" }
  ],
  "vote_average": 8.4,
  "runtime": 139
}
```

## Authentication
To authenticate your requests, you need an API key. Here are the steps to include the key:
- Sign up for an account on the MoviesDatabase website and obtain your API key.
- Include the API key as a query parameter or in the Authorization header.

### Example
- Query parameter:
  ```
  ?api_key=YOUR_API_KEY
  ```
- Authorization header:
  ```
  Authorization: Bearer YOUR_ACCESS_TOKEN
  ```

## Error Handling
The API uses standard HTTP status codes to indicate errors. Common errors include:
- **401 Unauthorized**: API key is missing or invalid.
- **404 Not Found**: The requested resource does not exist.
- **429 Too Many Requests**: Rate limit exceeded.

### Example Error Response
```json
{
  "status_code": 7,
  "status_message": "Invalid API key: You must be granted a valid key.",
  "success": false
}
```
To handle errors, check the HTTP status code and the `status_message` field in the response.

## Usage Limits and Best Practices
### Usage Limits
- The API imposes rate limits on requests. The default limit is **40 requests per 10 seconds**.
- Ensure your application adheres to these limits to avoid being temporarily blocked.

### Best Practices
- Cache frequent responses to reduce API calls.
- Use pagination for endpoints that return large datasets.
- Always check for errors and implement retry logic where appropriate.
- Secure your API key to prevent unauthorized access.

