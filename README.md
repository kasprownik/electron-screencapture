#electron-screencapture

Library that allows to take a picture or a video from any fragment of the display.

## API

### `takeScreenshot({x, y, width, height, sourceId})`
Takes static screenshot and returns promise with the result.

* `x, y, width, height` - these params define the rectangle of the frame
* `sourceId` - id of the display, primary display by default

####Example

```js
import {takeScreenshot} from "electron-screencapture";

takeScreenshot({x: 0, y: 0, width: 800, height: 600}).then(result => {
    console.log(result);
});
```

### `captureVideo({x, y, width, height, sourceId})`
Starts recording and returns promise with the object with the control api.

* `x, y, width, height` - these params define the rectangle of the frame
* `sourceId` - id of the display, primary display by default

####Control API object

* `stop()` - stops recording and returns promise with the video
* `pause()` - pauses recording
* `resume()` - resumes recording if paused

####Example

```js
import {captureVideo} from "electron-screencapture";

captureVideo({x: 0, y: 0, width: 800, height: 600}).then(recorder => {
    setTimeout(() => recorder.stop().then(result => {
        console.log(result);
    }), 1000);
});
```