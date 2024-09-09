# What does it do?

- Searches up the lyrics of a song with the [Lyrics.ovh](http://Lyrics.ovh) API
- Then the PurgoMalum API checks for any profanity within the lyrics
- Indicates if there is profanity in a song or not

# Requirements:

- [Lyrics.ovh](http://Lyrics.ovh) API - https://lyricsovh.docs.apiary.io/#reference/0/lyrics-of-a-song/search
- PurgoMalum API Profanity Check feature - https://www.purgomalum.com/index.html
- Python (Requests library)

# Instructions:

1. Run the Google Colab cells in order
2. Will be prompted to input the name of the song you want to check along with the artist
3. Will be notified if the song includes profanity or not for safe listening!

# Code Explanation:

### `getLyrics(artist, title)`

This function retrieves the lyrics for the specified song using the Lyrics.ovh API.

- **Parameters**: `artist` (str), `title` (str)
- **Returns**: Lyrics as a string if found, or `"No Lyrics Found"` if the song does not exist

### `containsProfanity(lyrics)`

This function checks if the provided lyrics contain profanity using the Purgomalum API.

- **Parameters**: `lyrics` (str)
- **Returns**:
    - `true` if profanity is detected.
    - `false` if no profanity is found.
    - `"Can't Check"` if there is an error with the API request.
