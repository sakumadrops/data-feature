# Explicit Song Checker
This python script retrieves the lyrics of a song and checks if there is profanity. It uses the Lyrics.ovh API to retrieve the lyrics and the PurgoMalum API to check for profanity.

# Purpose
If you haven't heard a song for the first time, you may not know whether it is explicit. This could be bad if you're playing a new playlist in front of a class or driving down the road with your strict parents! This script helps you quickly check a song for profanity.

# Features

- Searches up the lyrics of a song with the Lyrics.ovh API
- Then the PurgoMalum API checks for any profanity within the lyrics
- Indicates if there is profanity in a song or not

# APIs Used:

- Lyrics.ovh API - https://lyricsovh.docs.apiary.io/#reference/0/lyrics-of-a-song/search
- PurgoMalum API Profanity Check Feature - https://www.purgomalum.com/index.html

# Instructions:

1. Run the Google Colab cells in order
2. Will be prompted to input the name of the song you want to check along with the artist
3. Will be notified if the song includes profanity or not for safe listening!

# Code Explanation:

```python
def getLyrics(artist, title):
  url = f"https://api.lyrics.ovh/v1/{artist}/{title}"
  response = requests.get(url) 
  if response.status_code == 200:
    data = response.json()
    lyrics = data['lyrics']
    return lyrics
  else: 
    return "No Lyrics Found"
```

This function retrieves the lyrics for the specified song using the Lyrics.ovh API.

- **Parameters**: `artist` (str), `title` (str)
- **Returns**: Lyrics as a string if found, or `"No Lyrics Found"` if the song does not exist

```python
def containsProfanity(lyrics):
  url = f"https://www.purgomalum.com/service/containsprofanity?text={lyrics}"
  r = requests.get(url)
  if r.status_code == 200:
    return r.text 
  else:
    return "Cant Check"
```

This function checks if the provided lyrics contain profanity using the Purgomalum API.

- **Parameters**: `lyrics` (str)
- **Returns**:
    - `true` if profanity is detected.
    - `false` if no profanity is found.
    - `"Can't Check"` if there is an error with the API request.
