# Movie Barcode Generator

This is an updated version of the [Original Project](https://github.com/timbennett/movie-barcodes) so it works on Python 3, and is less heavy when generating output files (and you don't need to manually enter the width and height of the video).

![github-bighero6](https://cloud.githubusercontent.com/assets/1192790/11238640/1f7ea5ac-8e3b-11e5-8c2b-e00758b1ec19.png)

Turn video files into 'barcodes' where vertical lines represent the average colour of individual frames. [Example album.](http://imgur.com/gallery/Pw6LD/) Uses code [published by zulko](http://zulko.github.io/blog/2013/09/27/read-and-write-video-frames-in-python-using-ffmpeg/).

**Requirements:**
* [ffmpeg](https://www.ffmpeg.org/)
* Python 3
* [Python Imaging Library](http://www.pythonware.com/products/pil/)

**Usage:**  
    *python process_video.py inputfile*  
e.g.  
    *python process_video.py bigbuckbunny.mp4*

**Tips:**
* The output size is always number of processed frames x 100, you can change this if you want in the source code
* Sampling is always set at one frame every 4 seconds, again, you can change this in the source code.
* If it doesn't work on Windows, you might have to change FFMPEG_BIN from "ffmpeg" to "ffmpeg.exe"
* Use low resolution videos! They provide identical results but are processed exponentially faster than high definition videos. You're smearing all the details anyway.
* Due to the nature of PNG files, files will usually be quite small, even for large videos!
 
**Details:**

You may have seen sites like [moviebarcode](http://moviebarcode.tumblr.com/), [The Colors of Motion](http://thecolorsofmotion.com/) or the [Movie Barcode Generator](http://arcanesanctum.net/movie-barcode-generator/). In short, they compress a movie into a single image, with vertical lines representing the average colours of sequential frames. Ideally this gives a glanceable idea of the movie's colour palette.

While moviebarcode squashes each frame to a single pixel width (preserving some vertical gradients), this script uses a similar process to The Colors of Motion (a single colour per frame). First find the average RGB values of all pixels in a single frame:

![github-process-1](https://cloud.githubusercontent.com/assets/1192790/11238530/715e0d1e-8e3a-11e5-9736-68f2e67d21fc.png)

And then to repeat the process for all frames:

![github-process-2](https://cloud.githubusercontent.com/assets/1192790/11238535/7664e6ac-8e3a-11e5-8989-6be607fa395e.png)

This should work with any movie file ffmpeg can handle.

(Video stills: [Big Buck Bunny](https://peach.blender.org/download/))