# Audio File Tagger and Converter

This repository contains Python scripts for managing audio file metadata and converting between audio formats. The scripts are designed to work with FLAC and MP3 files, allowing you to tag audio files and convert between formats while preserving metadata.

## Features

- **FLAC Tagger**: Update metadata (tags) for FLAC audio files
- **FLAC to MP3 Converter**: Convert FLAC files to MP3 format while preserving metadata
- **Batch Processing**: Process multiple files in a directory
- **Metadata Preservation**: Maintains ID3 tags during conversion

## Requirements

- Python 3.6+
- Required Python packages (install using `pip install -r requirements.txt`):
  - mutagen
  - pydub
  - tqdm

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/engomaressam/tagging.git
   cd tagging
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### FLAC Tagger

```bash
python flac_tagger.py /path/to/audio/files
```

### FLAC to MP3 Converter

```bash
python flac_to_mp3.py /path/to/flac/files /output/directory
```

## Scripts

### flac_tagger.py

A script to update metadata (tags) for FLAC audio files. It can process a single file or all FLAC files in a directory.

### flac_to_mp3.py

A script to convert FLAC audio files to MP3 format while preserving metadata. It can process a single file or all FLAC files in a directory.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Author

Omar Essam
