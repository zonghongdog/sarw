# SARW - Set a random wallpaper

Download and set random downloaded wallpapers on Xfce4.

This is a toolchain, what written for set a random single & dual monitor wallpapers on multiple monitors.

The [`set-a-random-wallpaper.sh`](set-a-random-wallpaper.sh) wraps the whole process: download a random wallpaper with [***tool-1***](#tool-1-download-double-wide-wallpaper-from-wallpaperswidepy), crop for multi
monitor config with [***tool-2***](#tool-2-crop-wallpaper-for-multi-monitorspy), and set properly on all displays with [***tool-3***](#tool-3-set-multi-xfce4-wallpaperspy).

**Feel free, write your own walpaper setter "[***tool-3***](#tool-3-set-multi-xfce4-wallpaperspy)" and use this toolchain on non-Xfce desktop too!**

---

*Check my [UserScript](https://gist.github.com/andras-tim/d89344b843e9ebaeade5) what can change New Tab background in Google Chrome.*


## Usage

* Download and set a random wallpaper:

    ``` bash
    set-a-random-wallpaper.sh
    ```

  *This will downloads and holds one image per week*

* Download and set a new random wallpaper:

    ``` bash
    set-a-random-wallpaper.sh --new
    ```

  *This will remove the current image and download a new one*


## Tools

### [tool-1] [download-double-wide-wallpaper-from-wallpaperswide.py](download-double-wide-wallpaper-from-wallpaperswide.py)

Download a random double-wide wallpaper from [http://wallpaperswide.com/](http://wallpaperswide.com/3840x1080-wallpapers-r/)


#### Usage
**``download-double-wide-wallpaper-from-wallpaperswide.py <output_image_path>``**

* Download random wallpaper:

    ``` bash
    download-double-wide-wallpaper-from-wallpaperswide.py /tmp/test.jpg

    ```


### [tool-2] [crop-wallpaper-for-multi-monitors.py](crop-wallpaper-for-multi-monitors.py)

Crop double-wide wallpaper to left, center, right parts


#### Usage
**``crop-wallpaper-for-multi-monitors.py <source_path> <destination_path_prefix>``**

* **example input**:

    * ``wide_wallpaper.jpg`` 3840x1080 image file

* **example output**:

    * ``test-wallpaper_a-left.jpg`` 1920x1080, left crop of input file
    * ``test-wallpaper_b-right.jpg`` 1920x1080, right crop of input file
    * ``test-wallpaper_c-center.jpg`` 1920x1080, center crop of input file

``` bash
crop-wallpaper-for-multi-monitors.py 'wide_wallpaper.jpg' 'test-wallpaper'
```


### [tool-3] [set-multi-xfce4-wallpapers.py](set-multi-xfce4-wallpapers.py)

Set **Xfce4** wallpapers on multiple monitors


#### Configuration

Set placement of monitors by output in ``MONITOR_POSITIONS`` variable. The not specified monitors will use the *common*
wallpaper.


#### Usage
**``set-multi-wallpapers.py <common> [<left> <right>]``**

* Set the *common* wallpaper on all outputs:

    ``` bash
    set-multi-wallpapers.py '/path/common_wallpaper.jpg'
    ```

* Set wallpapers on all monitor according to ``MONITOR_POSITIONS``:

    ``` bash
    set-multi-wallpapers.py '/path/common_wallpaper.jpg' '/path/left_monitor_wallpaper.jpg' '/path/right_monitor_wallpaper.jpg'
    ```
