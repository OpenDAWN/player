# Player module

> WAVE audio library module for audio buffer playing.

The `player` object provides the following methods:

- `start()`
- `pause()`
- `stop() `
- `setBuffer(audioBuffer)`
- `setGain(float)`
- `setSpeed(float)`
- `seek(float)`
- `enableLoop(bool)`
- `on('ended', callback)`
- `getStatus()`


## Example

```js
    // Ensure global availability of an "audioContext" instance of web audio AudioContext.
    window.audioContext = window.audioContext || new AudioContext() || new webkitAudioContext();

    var player = new Player();
    var targetNode = audioContext.destination;
    player.connect(targetNode); // player unconnected by default

    var myBufferLoader = new BufferLoader(); // see our 'buffer-loader' module
    myBufferLoader.load('sound/file/path').then(
        function(audioBuffer){
            player.setBuffer(audioBuffer);
            player.start();
        }
    );


```

Note: our `BufferLoader` utility can be found at [https://github.com/Ircam-RnD/buffer-loader](https://github.com/Ircam-RnD/buffer-loader).

## API

The `player` object exposes the following API:

Method | Description
--- | ---
`player.start()` | Start playing.
`player.pause()` | Pause playing.
`player.stop()`  | Stop playing.
`player.setBuffer(audioBuffer)` | Set audio buffer to be played and internal `bufferDuration` property.
`player.setGain(float)` | Set internal `gain` property and apply a squared volume.
`player.setSpeed(float)` | Set playback speed.
`player.seek(float)` | Seek buffer position (in seconds).
`player.enableLoop(bool)` | Enable or disable looping playback.
`player.on('ended', function() { ... })` | Listen to the `'ended'` event.
`player.getStatus()` | Get player status (`IS_PLAYING`, `IS_PAUSED`, `IS_STOPPED`).

## Tests

If gulp is not installed

```bash
$ npm install -g gulp
```

Install all depencies in the module folder

```bash
$ npm install
```

Run the server on 9001 port (you can change the port in the Grunfile.js)

```bash
$ mocha tests/test.js
```

## License

This module is released under the [BSD-3-Clause license](http://opensource.org/licenses/BSD-3-Clause).

## Acknowledgments

This code is part of the WAVE project (http://wave.ircam.fr), funded by ANR (The French National Research Agency), *ContInt* program, 2012-2015.
