# Self-Hosted Media Server with Jellyfin using Docker on macOS
This project demonstrates how to self-host a media streaming server using Jellyfin on macOS via Docker.
It covers persistent volume mapping, library organization, metadata configuration, and custom lyrics options.

# Project Overview
Jellyfin is a free and open-source media system that lets you manage and stream your personal media collections (music, movies, TV shows, etc.) with ease.

This guide documents how to:

-> Deploy Jellyfin on macOS using Docker

-> Store configuration and media persistently

-> Add your music library with proper metadata

-> Enable lyrics and album art fetching

-> Troubleshoot and manage Docker containers

# Technologies Used
-> Docker: containerized deployment

-> Jellyfin: media server (using jellyfin/jellyfin Docker image)

-> macOS: host operating system

-> MusicBrainz, TheAudioDB: metadata and album art providers

# Project Structure
jellyfin/

├── config/   # Jellyfin config files (auto-generated)

├── cache/    # Cached metadata and artwork

├── music/    # Your personal music files

# Installation & Setup
Run the Jellyfin container with volume mapping for persistence:
docker run -d \
  --name jellyfin \
  -p 8096:8096 \
  -v ~/Downloads/jellyfin/config:/config \
  -v ~/Downloads/jellyfin/cache:/cache \
  -v ~/Downloads/jellyfin/music:/media/music \
  jellyfin/jellyfin
  
Explanation:

-p 8096:8096: exposes port 8096 for web access

Volume binds:

-> config for server settings

-> cache for metadata/artwork cache

-> music for your actual media library

-> Access the Jellyfin Dashboard

Open your browser and navigate to: http://localhost:8096

Complete the setup wizard:
1. Choose your preferred language
2. Create an admin user
3. Add a music library:
   
      -> Library path: /media/music

      -> Content type: Music

# Managing the Jellyfin Docker Container

| Action       | Command                              |
| ------------ | ------------------------------------ |
| Stop         | `docker stop jellyfin`               |
| Start        | `docker start jellyfin`              |
| View Logs    | `docker logs jellyfin`               |
| Remove       | `docker rm jellyfin`                 |
| Reset Config | `rm -rf ~/Downloads/jellyfin/config` |


# Learning Outcomes
-> Set up a local media streaming server with persistent data

-> Understood Docker volume binding and container management

-> Managed metadata services like lyrics and album artwork fetching

-> Gained troubleshooting experience with Docker containers

# License
This project is free to use and modify.

