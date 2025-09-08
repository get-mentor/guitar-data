# Audio Labeling Guide

This guide explains how to record, analyze, and label audio files for MIDI pitch detection.

## Recording and Analysis

1. **Record Audio**
   - Record audio in any format you prefer
   - Save the file as a WAV format
   - Open the file in a music editor (Audacity is free and recommended)

2. **Determine Note Properties**
   For each note and chord in your recording, use the editor to identify:
   - Start time of the note event
   - Stop time of the note event  
   - MIDI pitch of the notes

3. **Find MIDI Pitch Values**
   - In Audacity: Use **Effect > Pitch and Tempo > Change Pitch** to get the estimated frequency
   - Convert frequency to MIDI pitch using [this calculator](https://www.colincrawley.com/midi-note-to-audio-frequency-calculator/)
   - The calculator also plays frequencies so you can verify by ear

## File Naming

To avoid duplicate filenames, include one or more of the following:
- Unique random ID
- Timestamp
- Your name
- Audio descriptors (acoustic vs electric, lesson number, etc.)

**Example:** `guitar_acoustic_lesson1_john_20241201.wav`

## Creating Label Files

### CSV Structure
- Create a CSV file with the **exact same name** as your audio file, but with `.csv` extension
- Use [EditCSVOnline](https://www.editcsvonline.com/) to edit CSV files if needed
- Reference `example_label.csv` as a template
- Include headers in the first row

### CSV Format Requirements

**Headers:** `Note Event,Start Second,Start Millisecond,End Second,End Millisecond,Note Pitches`

- **Note Event:** Sequential numbers (1, 2, 3, etc.)
- **Start Second:** Integer values for start time in seconds
- **Start Millisecond:** Integer values for start time milliseconds  
- **End Second:** Integer values for end time in seconds
- **End Millisecond:** Integer values for end time milliseconds
- **Note Pitches:** MIDI pitch numbers in quotes

### Example CSV Structure
```csv
Note Event,Start Second,Start Millisecond,End Second,End Millisecond,Note Pitches
1,3,500,5,300,"60,64,67"
2,5,300,10,0,"60"
3,90,0,95,0,"62,65"
```

### Time Formatting Examples
- A chord starting at 3.5 seconds and ending at 5.0 seconds:
  - Column 2: `3`
  - Column 3: `500`
  - Column 4: `5`
  - Column 5: `0`

### MIDI Pitch Formatting
- **Single note:** `"60"`
- **Multiple notes:** `"60,64,67"` (comma-separated, no spaces)
- **Always use quotes** around pitch values
- **Don't include spaces** after commas

## File Organization

Upload files to the appropriate repository folder:

### Folder Structure
- **`unlabeled/`** - Audio files without label files
- **`unverified/`** - Audio files with label files (needs verification)
- **`verified/`** - Audio files with verified, correct labels

### Workflow
1. Upload audio + label files to `unverified/` folder
2. Upload audio-only files to `unlabeled/` folder
3. **If you have time:**
   - Verify files in `unverified/` folder for accuracy
   - Move correctly labeled files to `verified/` folder
   - Create labels for files in `unlabeled/` folder and move to `unverified/`

## Quality Notes
- Aim for reasonable accuracy in timing
- Small differences (a few milliseconds) won't significantly impact results
- 1 millisecond precision is extremely fine - don't over-optimize
