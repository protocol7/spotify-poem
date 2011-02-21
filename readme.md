Inspired by [http://spotifypoetry.tumblr.com], poem.py takes a poem and will attempt to match up a Spotify playlist with track names making up the poem. 

To run, you need to have Python 3.1 installed. If you do not already have this, you can find instructions here [http://diveintopython3.org/installing-python.html]

After everything is set up, simply run (feel free to choose a poem of your choosing :-):

    python3.1 poem.py "STRANGER! if you, passing, meet me, and desire to speak to me, why should you not speak to me?"

As the program runs, you will the poem with matching tracks will be printed to your terminal. Some searches might take quite some time, so be patient :-)

## Implementation notes
* Poems are delimited into sentences where punctuation characters (e.g. ".", ",", "!") are found. Track matching is done on sentences, or part of.
* Searches support UTF-8, but will might incorrectly delimit sentences containing non-ASCII whitespace characters. The search is case-insensitive. 
* The search algorithm will attempt to find the optimal match (fewest tracks per sentence). Currently, it will attempt the full search space, which for long sentences can mean quite a few searches (and thus long search times) but that it will (finally) find the optimal result. 
* Searches results will be cached according to the cache headers sent by Spotify. That means that repeated searches (possibly on the word level) will not go over the network and therefore be much faster.
* The Spotify API is not optimal for this type of application. Some simple searches will simply not find a result, even though a match exists in the Spotify database. Such an example is the search for "And I" which will fail to locate a match using the API (at least among the 2000 first results). However, using the client will find several matches in the first search result (e.g. spotify:track:1Jp9n1uHB72CfK31j4mEPh).