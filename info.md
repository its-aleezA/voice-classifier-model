# Data Information and Changelog

## Changelog for version 16
1. Added new file `feat_bts.csv` for songs that BTS is featured in. It has a subset of the columns.
2. Added albums: Killin' It Girl (feat. GloRilla) (Remixes), PERMISSION TO DANCE ON STAGE - LIVE

## Additional Notes
* Spotify has deprecated the [Audio Features API](https://developer.spotify.com/blog/2024-11-27-changes-to-the-web-api), which may cause future files to not have information for columns with the `spotify_track_` prefix

## Columns
* id (string) : unique identifier for each track
  * In the format: `<GROUP>-<NUM>` where `GROUP` is either BTS/member’s name/FEAT(uring) and `NUM` is generated sequential number
* album_title (string) : title of the album
* eng_ album_title (string) : title of album without non-english characters
* album_rd (string) : date that album was released in isoformat (YYYY-MM-DD)
* album_seq (int) : sequence of track in album
* track_title (string) : title of the track
* raw_track_title (string): title of the track with non-english characters
* eng_track_title (string) : title of the track without non-english characters
* lyrics (string) : english translated lyrics of the track (from genius, unlessly otherwise credited in columns `eng_lyrics_source_url` and `eng_lyrics_credits`)
  * will be empty for instrumentals
* hidden_track (boolean) : indicates whether the track is a hidden track
  * hidden tracks usually refer to tracks that are exclusives to the physical album and not on music streaming services but are in the official album tracklists
* remix (boolean) : indicates whether the track is a remix
* featured (string) : indicates who is featured in the track
  * For members' solo tracks, if another BTS member is stated as featured on the track, they will be listed in the `performed_by` column and not this column
  * for `feat_bts.csv`, this column details which BTS member / BTS is featured
* performed_by (string) : indicates who in BTS performed the track
  * multiple individuals seperated with ";" (e.g. RM;SUGA;J-HOPE would mean that the track is performed by RM, SUGA and J-HOPE) (yes, I'm using stage names)
  * BTS: the whole group
  * featured non-BTS members artists will not be reflected in this column
  * for instrumentals, this column will be empty
  * for `feat_bts.csv`, this column contains the artist(s) of the song
* repackaged (boolean) : indicates if the track was already released in an earlier album
* lang (string) : language of track according to the ISO 639-2 (alpha 3) codes
  * KOR: Korean
  * ENG: English
  * JPN: Japanese
  * NA: Not Applicable (e.g. instrumentals)
* has_full_ver (boolean) : indicates if the track has a full version
  * demo versions will also have value TRUE in this column
* is_alt_lang_ver (boolean) : indicates if the track is of a preciously existing track but in a different language
* spotify_album_id (string) : [Spotify's base-62 identifier for the album](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids)
* spotify_track_duration_ms (int) : [the track's duration in milliseconds](https://developer.spotify.com/documentation/web-api/reference/get-track)
* spotify_track_id (string) : [Spotify's base-62 identifier for the track](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids)
* spotify_track_danceability (float) : [describes how suitable a track is for dancing](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
  * Value ranges from 0.0 (least danceable) to 1.0 (most danceable)
* spotify_track_energy (float) : [represents a perceptual measure of intensity and activity](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
  * Value ranges from 0.0 (less energy) to 1.0 (more energy)
  * Tracks with higher energy tend to feel faster, louder and noiser  
* spotify_track_key (int) : [key the track is in according to the Pitch Class notation](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
  * [Pitch class notation](https://en.wikipedia.org/wiki/Pitch_class): C - 0, C♯/D♭ = 1, D = 2, D♯/E♭ = 3, E = 4, F = 5, F♯/G♭ = 6, G = 7, G♯/A♭ = 8, A = 9, A♯/B♭ = 10, B = 11 
  * If no key was detected, the value is -1
* spotify_track_loudness (float) : [overall loudness of a track in decibels (dB)](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
* Values typically range between -60 to 0 db
* spotify_track_mode (int) : [indicates the modality (major or minor) of a track](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
  * Major is represented by 1 and minor is 0
* spotify_track_speechiness (float) : [detects the presence of spoken words in a track](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
    * Value ranges from 0.0 (less words) to 1.0 (more words)
    * Values above 0.66 describe tracks that are probably made entirely of spoken words. Values between 0.33 and 0.66 describe tracks that may contain both music and speech, either in sections or layered, including such cases as rap music. Values below 0.33 most likely represent music and other non-speech-like tracks.
* spotify_track_acousticness (float) : [confidence measure of whether the track is acoustic](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
  * Values range from 0.0 (low confidence that the track is acoustic) to 1.0 (high confidence that the track is acoustic)
* spotify_track_instrumentalness (float) : [predicts whether a track contains no vocals](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
    * "Ooh" and "aah" sounds are treated as instrumental in this context
    * Rap or spoken word tracks are clearly "vocal". The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content. Values above 0.5 are intended to represent instrumental tracks, but confidence is higher as the value approaches 1.0.
* spotify_track_liveness (float) : [detects the presence of an audience in the recording](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
  * Values range from 0.0 to 1.0 (high probability that track was performed live)
  * A value above 0.8 provides strong likelihood that the track is live.
* spotify_track_valence (float) : [describes the musical positiveness conveyed by a track](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
  * Values range from 0.0 (sounds more negative (e.g. sad, depressed, angry)) to 1.0 (sounds more positive (e.g. happy, cheerful, euphoric))
* spotify_track_tempo (float) : [overall estimated tempo of a track in beats per minute (BPM)](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
* spotify_track_time_signature : [estimated time signature (number of beats per bar / measure)](https://developer.spotify.com/documentation/web-api/reference/get-audio-features)
  * Values range from 3 (3/4) to 7 (7/4)
* eng_lyrics_source_url : indicates the URL of the english translated lyrics if the translations are not retrieved from Genius
* eng_lyrics_credits : indicates any required credits of the english translated lyrics if the translations are not retrieved from Genius

## `bts.csv`
### Changelog
1. Version numbering removed from file name

### Albums (54)
* 2 Cool 4 Skool
* O!RUL8,2?
* Skool Luv Affair
* Skool Luv Affair (Special Addition)
* No More Dream (Japanese Ver.)
* Boy In Luv (Japanese Ver.)
* Dark and Wild
* Danger (Japanese Ver.- / Standard Edition)
* MIC Drop (feat. Desiigner) [Steve Aoki Remix]
* Wake Up (Standard Edition)
* 화양연화 The Most Beautiful Moment In Life Pt.1
* For You
* 화양연화 The Most Beautiful Moment In Life Pt.2
* I Need U (Japanese Ver. / Standard Edition)
* Run (Japanese Ver./Standard Edition)
* 화양연화 The Most Beautiful Moment In Life: Young Forever
* Youth
* WINGS
* You Never Walk Alone
* 血、汗、涙
* Come Back Home
* Love Yourself 承 'Her'
* MIC Drop/DNA/Crystal Snow
* FACE YOURSELF
* LOVE YOURSELF 轉 'Tear'
* FAKE LOVE (Rocking Vibe Mix)
* LOVE YOURSELF 結 'Answer'
* FAKE LOVE/Airplane pt.2
* MAP OF THE SOUL: PERSONA
* Dream Glow (BTS World Original Soundtrack) (Pt. 1)
* A Brand New Day (BTS World Original Soundtrack) (Pt. 2)
* All Night (BTS World Original Soundtrack) (Pt. 3)
* BTS WORLD: Original Soundtrack
* Lights/Boy With Luv
* Black Swan
* MAP OF THE SOUL: 7
* Stay Gold
* MAP OF THE SOUL : 7 ~ THE JOURNEY ~
* Dynamite (DayTime Version)
* Dynamite (NightTime Version)
* BE
* Dynamite (Holiday Remix)
* Film out
* Butter (Hotter, Sweeter, Cooler)
* BTS THE BEST
* Butter / Permission to Dance
* Permission to Dance
* Butter (Megan Thee Stallion Remix)
* Butter (Holiday Remix)
* Proof
* Yet To Come (Hyundai Ver.)
* The Planet
* Take Two
* PERMISSION TO DANCE ON STAGE - LIVE 🆕

## `jin.csv`
### Changes
1. Version numbering removed from file name

### Notes
* There are 2 albums (singles) named "Super Tuna", both are kept in the dataset as the earlier release was pulled and the track was re-released in an extended formet.
  * The earlier release (`JIN-7`) has field `has_full_ver = TRUE` to reflect this as well

### Albums (19)
* HWARANG, Pt. 2 (Music from the Original TV Series)
* Tonight
* Abyss
* Jirisan (Original Television Soundtrack) Pt. 4
* Super Tuna
* The Astronaut
* Super Tuna
* I'll Be There
* Happy
* Happy - :') (Remixes)
* Happy - :D (Remixes)
* Running Wild (Remixes)
* Falling (feat. Taka)
* When the Stars Gossip OST Part.3
* Echo
* Don't Say You Love Me (Remixes)
* Echo (+1db)
* Echo (+2db)
* Echo (+3db)

## `suga.csv`
### Changelog
1. Version numbering removed from file name

### Albums (4)
* Agust D
* D-2
* People Pt.2 (feat. IU)
* D_DAY

## `rm.csv`
### Changelog
1. Version numbering removed from file name

### Albums (7)
* RM
* Change
* Bicycle
* mono.
* Indigo  
* Come back to me
* Right Place Wrong Person

## `jhope.csv`
### Changelog
1. Version numbering removed from file name

### Albums (16)
* Hope World
* Chicken Noodle Soup (feat. Becky G)
* Blue Side
* MORE
* Jack In The Box
* on the street (with J. Cole)
* Jack In The Box (HOPE Edition)
* HOPE ON THE STREET VOL.1
* Sweet Dreams (feat. Miguel)
* Sweet Dreams (zzZ Remixes)
* Sweet Dreams (feat. Miguel) (FNZ Remix)
* MONA LISA
* MONA LISA (Remixes)
* MONA LISA (Remix so fine)
* Killin' It Girl (feat. GloRilla)
* Killin' It Girl (feat. GloRilla) (Remixes) 🆕

## `jimin.csv`
### Changelog
1. Version numbering removed from file name

### ALbums (13)
* Promise
* Christmas Love
* Our Blues, Pt. 4 (Original Television Soundtrack)
* Closer Than This
* Set Me Free Pt.2
* FACE
* Like Crazy (Remixes)
* Smeraldo Garden Marching Band (feat. Loco)
* MUSE
* MUSE (WANDER ver.)
* MUSE (WONDER ver.)
* Who (Remixes)
* Be Mine (English Version)

## `v.csv`
### Changelog
1. Version numbering removed from file name

### Albums (14)
* HWARANG, Pt. 2 (Music from the Original TV Series)
* Scenery
* Winter Bear
* ITAEWON CLASS (Original Television Soundtrack) Pt. 12
* Snow Flower (feat. Peakboy)
* Our Beloved Summer (Original Television Soundtrack), Pt. 5
* Layover
* Slow Dancing (Remixes)
* FRI(END)S
* Winter Ahead (with PARK HYO SHIN)
* Winter Ahead (with PARK HYO SHIN) : Silent Carol Ver.
* White Christmas (Instrumental)
* White Christmas (with V of BTS)
* Winter Ahead (with PARK HYO SHIN) : YUNSEOKCHEOL TRIO Ver.

## `jungkook.csv`
### Changelog
1. Version numbering removed from file name

### Albums (11)
* Seven (Weekend Ver.)
* Seven (feat. Latto) (Alesso Remix)
* 3D (feat. Jack Harlow)
* 3D : The Remixes
* TOO MUCH
* 3D (feat. Jack Harlow) (MK Remix)
* Seven (feat. Latto) (David Guetta Remix)
* GOLDEN
* Standing Next to You (The Remixes)
* 3D (Justin Timberlake Remix)
* Standing Next to You (Usher Remix)
* Never Let Go