# Watcher Docker Container

Docker container for [Watcher](https://github.com/nosmokingbandit/watcher) using a lightweight Fedora build.

Watcher is an automated movie NZB searcher and snatcher. You can add a list of wanted movies and Watcher will automatically send the NZB to Sabnzbd or NZBGet. Watcher also has basic post-processing capabilities such as renaming and moving.

Watcher is a work in progress and plans to add more features in the future, but we will always prioritize speed and stability over features.

## Usage 

```bash
docker create 
-v /path/to/config/dir:/config
-v /path/to/log/dir:/log
-v /path/to/movie/dir:/movie
-v /path/to/download/dir:/downloa
-e LUID=1234 -e LGID=1234
    -p 9090:9090 --name=Watcher 
```

Due Note: The download directory needs to be the full path that your downloader (SabNZB or NZBGet) passes to the renamer to tell it where the file is located. 

Example: I use nzbget and when a movie is finished it says where the file is located so Watcher can take that and move it. 

"path": "/volume2/Storage/NZBGet/Watcher/MOVIENAME 

That is what NZBGet reports to Watcher. So for our config when settings up docker we need to use

-v /Storage/NZBGet/Watcher:/volume2/Storage/NZBGet/Watcher

This way when Watcher gets told the directory, docker will mount the same pathing for Watcher to access the files. 

# Post-processing Scripts


You will have to manually download the post processing scripts from:
https://github.com/nosmokingbandit/watcher

You can locate the scripts in the [post scripts](https://github.com/nosmokingbandit/watcher/tree/master/post%20scripts) folder. 


From there you will have to take the NZBGet or Sabnzb scripts and put them in your appropriate install directory for your choice of downloader. 


