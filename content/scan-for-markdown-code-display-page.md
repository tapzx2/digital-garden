---
tags:
  - public
---

```bash
#!/bin/bash

# Variable to fill in the target directory
TARGET_DIR="~/repo/quartz/content"
SOURCE_DIR="~/remote-brain"
LOG_FILE="process_log.txt"

# Initialize log file
echo "Process started at $(date)" > $LOG_FILE

# Function to process markdown files
process_markdown() {
    local file=$1
    local base_dir=$(dirname "$file")

    #echo "Processing file: $file" >> $LOG_FILE

    # Check for the public tag in the front-matter
    if awk '/^---/{f=!f} f && /tags:/,/^---/' "$file" | grep -q '\- public'; then
        echo "Found public tag in $file" >> $LOG_FILE

        # Copy the file to the target directory
        cp "$file" "$TARGET_DIR"
        echo "Copied $file to $TARGET_DIR" >> $LOG_FILE

        # Scan for Obsidian-style links [[link]]
        #grep -o '\[\[.*\]\]' "$file" | while read -r link; do
            # Remove the [[ and ]]
        #    link=$(echo "$link" | sed 's/\[\[//;s/\]\]//')

            # Find the linked markdown file
        #    linked_file=$(find "$SOURCE_DIR" -name "$link.md")

            # Process the linked file
        #    if [ -n "$linked_file" ]; then
        #        process_markdown "$linked_file"
        #    fi
        #done

        # Scan for Obsidian-style media files ![[media]]
        grep -o '!\[\[[^]]*\]\]' "$file" | while read -r media_link; do
            # Remove the ![[ and ]]
            media=$(echo "$media_link" | sed 's/!\[\[//;s/\]\]//')

            # Log the found media link
            echo "Found media link: $media" >> $LOG_FILE

            # Find the linked media file
            media_file=$(find "$SOURCE_DIR" -name "$media")

            # Log the path of the linked media file
            if [ -n "$media_file" ]; then
                echo "Found media file: $media_file" >> $LOG_FILE

                # Copy the media file to the target directory
                cp "$media_file" "$TARGET_DIR/media-files/"
                echo "Copied media file $media_file to $TARGET_DIR/media-files/" >> $LOG_FILE
            else
                echo "No media file found for: $media" >> $LOG_FILE
            fi
        done
    fi
}

# Function to clean up TARGET_DIR
cleanup_target_dir() {
    echo "Cleaning up $TARGET_DIR" >> $LOG_FILE

    # Find all files in TARGET_DIR
    find "$TARGET_DIR" -type f | while read -r target_file; do
        target_file_name=$(basename "$target_file")

        # Check if the file exists in SOURCE_DIR
        if ! find "$SOURCE_DIR" -name "$target_file_name" | grep -q .; then
            # If the file does not exist in SOURCE_DIR, delete it from TARGET_DIR
            rm "$target_file"
            echo "Deleted $target_file from $TARGET_DIR" >> $LOG_FILE
        fi
    done
}

# Create the media-files directory if it doesn't exist
mkdir -p "$TARGET_DIR/media-files"

# Cleanup target directory before processing
cleanup_target_dir

# Find all markdown files in the source directory
find "$SOURCE_DIR" -name "*.md" | while read -r file; do
    process_markdown "$file"
done
```

```embed-bash
PATH: "vault://code/obsidian-publishing/scan-for-mkdown.sh"
TITLE: "scan for markdown" 
```