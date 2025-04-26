![Unity](/unity-brand.jpg?raw=true "Unity")

# Unity WebGL Server

Welcome to the Unity WebGL Nginx Server!  
This repository contains everything needed to serve a Unity WebAssembly (WASM) WebGL build efficiently using Nginx with
Brotli and Gzip compression.

Table of contents
=================

<!--ts-->

* [About](#about)
* [Assets Included](#assets-included)
* [Installation and Running](#installation-and-running)
* [Credits](#credits)

<!--te-->

## About

This project sets up an optimized Nginx server ready to host Unity WebGL builds.  
It automatically serves compressed assets (Brotli `.br` or Gzip `.gz`) if available, and falls back to plain
uncompressed files when necessary.

**Why?**

- Improve load times with compressed assets
- Take full advantage of modern browser capabilities (Brotli/Gzip support)
- Simplify deployment and local testing of Unity WebGL projects

---

## Assets Included

The server handles three types of builds:

| Folder | Description                                                                  |
|:-------|:-----------------------------------------------------------------------------|
| `/gz`  | Gzip-compressed version of the build. NOTE: Only accessible through port 443 |
| `/br`  | Brotli-compressed version of the build (best performance)                    |

Depending on the request and client support (Accept-Encoding header), Nginx will serve the correct version.

---

## Installation and Running

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

### 2. Build and run with Docker

```bash
docker-compose up -d
```

**This will:**

- Start the Nginx container
- Expose ports 80 (HTTP) and 443 (HTTPS)
- Serve files from the web/ folder

### 3. Access your Unity WebGL build
1. Open your browser and go to: http://localhost
2. Navigate to /plain/, /gz/, or /br/ depending on what you want to test

Example: `http://localhost/br`

## Credits
- Francisco Carvalho @fiskolini
- Kendir Studios [kendirstudios.pt 🇵🇹](kendirstudios.pt)
- Unity Technologies for Unity WebGL 
- Nginx for high-performance web serving
- `fholzer/nginx-brotli` for the Nginx image with Brotli support

Made with ❤️ to boost your WebGL experience.