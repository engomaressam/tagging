# tagging: FLAC tagger and FLAC-to-MP3 converter

Two small Python tools for a music library kept as one folder per album:

- **`flac_tagger.py`** sets the album tag and genre on every FLAC file and embeds the album's cover art.
- **`flac_to_mp3.py`** converts a whole FLAC library to 320 kbps MP3. It keeps the tags and cover art and mirrors the
  folder structure.

Both open a folder picker (Tkinter), so they take no command-line arguments.

## Expected layout

```
Music/
├── Artist A/
│   └── Album One/
│       ├── 01 - First Track.flac
│       ├── 02 - Second Track.flac
│       └── coverart.jpg        # optional
└── Artist B/
    └── Album Two/
        └── ...
```

## flac_tagger.py

1. Pick the top folder. Every subfolder that holds `.flac` files is treated as one album.
2. Enter one genre. It is applied to all albums in that run.
3. For each FLAC file it sets `album` to the folder's name and `genre` to your genre. If `coverart.jpg` is in the
   folder, it replaces the embedded pictures with it as the front cover, converting RGBA images to RGB JPEG first.

It edits the files in place (with [mutagen](https://mutagen.readthedocs.io/)), so try it on a copy first.

## flac_to_mp3.py

1. Pick the source FLAC folder, then the destination folder.
2. It walks the source tree and recreates each album folder under the destination. It copies `coverart.jpg` and
   converts every track with ffmpeg in parallel (a thread pool):
   `ffmpeg -i in.flac -ab 320k -map_metadata 0 -id3v2_version 3 out.mp3`.
3. It checks every output file, deletes empty or partial ones, and lists the failed tracks album by album at the end.

## Setup

```bash
git clone https://github.com/engomaressam/tagging.git
cd tagging
pip install -r requirements.txt
```

`flac_to_mp3.py` also needs [ffmpeg](https://ffmpeg.org/download.html) on the PATH.

```bash
python flac_tagger.py
python flac_to_mp3.py
```

## License

MIT, see [LICENSE](LICENSE).
