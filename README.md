Video Player plugin for Cordova/PhoneGap
========================================

A Cordova plugin that simply allows you to immediately play a video in fullscreen mode.

# 修該版本

# Installation

將 plugin 放到 cordova 目錄內

```
cordova plugin add ./SignagePlayer --link
```

## Example

```javascript
VideoPlayer.play(
    "file:///android_asset/www/movie.mp4",
    {
        volume: 0.5,
        scalingMode: VideoPlayer.SCALING_MODE.SCALE_TO_FIT_WITH_CROPPING,
		looping: true,
        fullScreenMode: true,
        gravity: 'center'
    },
    function () {
        console.log("video completed");
    },
    function (err) {
        console.log(err);
    }
);
```

## Options

- `volume`: (Optional) allows you to set the volume on this player. Note that the passed volume value is raw scalars in range 0.0 to 1.0.

- `scalingMode`: (Optional) allows you to sets video scaling mode.

    The following constants are the only values available for the `scalingMode` option:

    - `SCALE_TO_FIT` (default)
    - `SCALE_TO_FIT_WITH_CROPPING`

    Refer to http://developer.android.com/reference/android/media/MediaPlayer.html#setVideoScalingMode(int) for more details.

- `looping`: (Optional) sets the player to be looping or non-looping. Default: ```true```

- `fullScreenMode`: (Optional) 全螢幕顯示 Default: ```true```

- `gravity`: (Optional) 顯示位置 Default: ```center```

	- `center` (default): Gravity.CENTER
    - `top_left`	: Gravity.TOP | Gravity.LEFT
	- `top_right`	: Gravity.TOP | Gravity.RIGHT
    - `bottom_left`	: Gravity.BOTTOM | Gravity.LEFT
	- `bottom_right`: Gravity.BOTTOM | Gravity.RIGHT
	
- `width`: (Optional)(Int) 影片顯示寬度

- `height`: (Optional)(Int) 影片顯示高度

- `x`: (Optional)(Int) 影片X軸位置

- `y`: (Optional)(Int) 影片y軸位置


# Installation(原生)

This plugin use the Cordova CLI's plugin command. To install it to your application, simply execute the following (and replace variables).

```
cordova plugin add https://github.com/vmartins/cordova-plugin-videoplayer
```


# Using(原生)

Just call the  `play` method with a video file path as argument. The video player will close itself when the video will be completed.

```
VideoPlayer.play(path, [options], [completeCallback], [errorCallback]);
```

Stop and close a video currently playing without waiting the end.
```
VideoPlayer.close();
```

The plugin is able to play file-path or http/rtsp URL.

You can optionally add options parameters like volume and calling mode.
You can also add an success callback function to handle completed playback.
You can also add an error callback function to handle unexpected playback errors.

## Example(原生)

```javascript
VideoPlayer.play("file:///android_asset/www/movie.mp4");
```

```javascript
VideoPlayer.play(
    "file:///android_asset/www/movie.mp4",
    {
        volume: 0.5,
        scalingMode: VideoPlayer.SCALING_MODE.SCALE_TO_FIT_WITH_CROPPING
    },
    function () {
        console.log("video completed");
    },
    function (err) {
        console.log(err);
    }
);
```

## Options(原生)

- `volume`: (Optional) allows you to set the volume on this player. Note that the passed volume value is raw scalars in range 0.0 to 1.0.

- `scalingMode`: (Optional) allows you to sets video scaling mode.

    The following constants are the only values available for the `scalingMode` option:

    - `SCALE_TO_FIT` (default)
    - `SCALE_TO_FIT_WITH_CROPPING`

    Refer to http://developer.android.com/reference/android/media/MediaPlayer.html#setVideoScalingMode(int) for more details.

- `looping`: (Optional) sets the player to be looping or non-looping. Default: ```false```

# Troubleshooting

**When playing a video for the first time, everything works great. when calling .close() function the video closes great. 2nd time around, the .play() is called the same way as the first time. The video plays fine for the second time. Now when trying to close it before the video ends, the app fatally crash.**

When the "completed" event gets fired, make sure you close the video in the "completed" event to clear that instance so that if you have another video they don't both play.


# Licence MIT

Copyright 2013 Quentin Aupetit

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
