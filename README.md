A Fork of Video-JS-SWF for the Clip Web Player
============

This fork surfaces makes two changes to the Video JS SWF:

1. Abacast uses Flash's [onMetaData](http://help.adobe.com/en_US/AS2LCR/Flash_10.0/help.html?content=00001405.html)
event to surface synced banner ads from their Flash video stream. In the
original Video JS SWF only the first onMetaData is emitted from Flash as a 
loadedmetadata event.  Additional onMetaData events are ignored. However we need
additional onMetaData events from Flash to be emitted to the external interface.  
So this fork makes a change to emit additional onMetaData events as a custom 
metadataupdated event passing the data from the Flash video stream to the 
external interface so that synced banner ads can be displayed when appropriate.
2. As noticed in this [issue](https://github.com/videojs/video-js-swf/issues/148)
pausing the stream will not stop the Flash video from downloading, which is 
wasteful. So we address that here in our fork.

The light-weight Flash video player that makes Flash work like HTML5 video. This allows player skins, plugins, and other features to work with both HTML5 and Flash

This project doesn't need to be used if you simply want to use the Flash video player.  Head back to the main Video.js project if that's all you need, as the compiled SWF is checked in there.

Installation
============

1. Install Node Packages.
```bash
    npm install
   ```
2. Compile SWF.
Development (places new SWF in /dist/):
```bash
    grunt mxmlc
   ```
Production/ Distribution (runs mxmlc task and copies SWF to dist/):
```bash
    grunt dist
   ```
3. Run Connect Server.
```bash
    grunt connect:dev
```
4. Open your browser at [http://localhost:8000/index.html](http://localhost:8000/index.html) to see a video play.  You can keep using grunt to rebuild the Flash code.


Running Unit and Integration Tests
===========

** Note - We want to drop all of this for grunt based / Karma testing.

For unit tests, this project uses [FlexUnit](http://flexunit.org/). The unit tests can be found in [project root]/src/com/videojs/test/

For integration tests, this project uses [qunit](http://qunitjs.com/). The integration tests can be found in [project root]/test

In order to run all of the tests, use the links at  [http://localhost:8000/index.html](http://localhost:8000/index.html)

There are very few tests.  Adding to them is a fantastic and much appreciated way to contribute.
