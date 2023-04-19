# Extra Changings
updated: 2023.04.18
- Added `download_path` argument to allow setting the download path directly.
- Added `keyword` argument for allowing the use of different keyword files. (*.txt only)

# Changes on this Fork
updated: 2023.03.02 / ChromeDriver 110.0.5481.178

- Fixed bug on `google` & `google_full`
- Add `transparents` arguments that filters transparent images only. (for google)
- Fixed a bug that `limit` does not work on `google_full`
- Fixed a bug that multiprocess threads did not exit when `Ctrl+C` is pressed

### Best usage of this Fork
```
python3 main.py --google true --transparent true --naver false --full true #[--no_gui false] [--limit 100]
```
And now whenever you can stop program by pressing `Ctrl+C`! 

# AutoCrawler
Google, Naver multiprocess image crawler (High Quality & Speed & Customizable)

![](docs/animation.gif)

# How to use

1. Install Chrome

2. pip install -r requirements.txt

3. Write search keywords in keywords.txt

4. **Run "main.py"**

5. Files will be downloaded to 'download' directory.


# Arguments
usage:
```
python3 main.py [--skip true] [--threads 4] [--google true] [--naver true] [--transparent false] [-- download_path download] [--keyword keywords.txt] [--full false] [--face false] [--no_gui auto] [--limit 10]
```

```
--skip true                 Skips keyword if downloaded directory already exists.
                            This is needed when re-downloading.

--threads 4                 Number of threads to download.

--google true               Download from google.com (boolean)

--naver true                Download from naver.com (boolean)

--transparent false         Filter for transparent background images(for google)

--download_path download    Download Path for crawled data.
                            (Class directories are generated automatically.)

--keyword keywords.txt      Keyword file path. (File extension must be *.txt)

--full false                Download full resolution image instead of thumbnails (slow)

--face false                Face search mode

--no_gui auto               No GUI mode. (headless mode) Acceleration for full_resolution mode,
                            but unstable on thumbnail mode.
                            Default: "auto" - false if full=false, true if full=true
                            (can be used for docker linux system)
                   
--limit 0                   Maximum count of images to download per site. (0: infinite)
--proxy-list ''             The comma separated proxy list like:
                            "socks://127.0.0.1:1080,http://127.0.0.1:1081".
                            Every thread will randomly choose one from the list.
```


# Full Resolution Mode

You can download full resolution image of JPG, GIF, PNG files by specifying --full true

![](docs/full.gif)



# Data Imbalance Detection

Detects data imbalance based on number of files.

When crawling ends, the message show you what directory has under 50% of average files.

I recommend you to remove those directories and re-download.


# Remote crawling through SSH on your server

```
sudo apt-get install xvfb <- This is virtual display

sudo apt-get install screen <- This will allow you to close SSH terminal while running.

screen -S s1

Xvfb :99 -ac & DISPLAY=:99 python3 main.py
```

# Customize

You can make your own crawler by changing collect_links.py

# Issues

As google site consistently changes, please make issues if it doesn't work.
