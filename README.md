# @lucassilbernagel/react-audio-recorder

Forked from [@sarafhbk/react-audio-recorder](https://www.npmjs.com/package/@sarafhbk/react-audio-recorder)

> This is a simple audio recorder package for react application using the javascript [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API).

# Demo

Checkout the [Demo.](https://LucasSilbernagel.github.io/react-audio-recorder)

## Install

```bash

npm install --save @lucassilbernagel/react-audio-recorder

```

## Props

| Property name   | Type   | Default            | Description                           |
| --------------- | ------ | ------------------ | ------------------------------------- |
| status          | string | RECORD_STATUS.IDLE | RECORD_STATUS.(IDLE,RECORDING,PAUSED) |
| audioResult     | string | -                  | Result blob url.                      |
| errorMessage    | string | -                  | Error messages.                       |
| timer           | number | -                  | Record timer (in secs).               |
| startRecording  | method | -                  | Call this method to start recording.  |
| stopRecording   | method | -                  | Call this method to stop recording.   |
| pauseRecording  | method | -                  | Call this method to pause recording.  |
| resumeRecording | method | -                  | Call this method to resume recording. |

## Usage (Class Version)

```tsx
import React, { Component } from 'react'

import { ReactAudioRecorder } from '@lucassilbernagel/react-audio-recorder'

class Example extends Component {
  render() {
    return (
      <ReactAudioRecorder
        render={({
          timer,
          stopRecording,
          startRecording,
          resumeRecording,
          pauseRecording,
          audioResult,
          status,
          errorMessage
        }) => (
          <div>
            <audio controls src={audioResult} />
            <p>
              Status : <b>{status}</b>
            </p>
            <p>
              Error Message : <b>{errorMessage}</b>
            </p>
            <div>
              <p>{new Date(timer * 1000).toISOString().substr(11, 8)}</p>
              <div>
                <button onClick={startRecording}>Start</button>
                <button onClick={stopRecording}>Stop</button>
                <button onClick={pauseRecording}>Pause</button>
                <button onClick={resumeRecording}>Resume</button>
              </div>
            </div>
          </div>
        )}
      />
    )
  }
}
```

## Usage (Hooks Version)

```tsx
import React from 'react'

import { useAudioRecorder } from '@lucassilbernagel/react-audio-recorder'

function Example() {
  const {
    audioResult,
    timer,
    startRecording,
    stopRecording,
    pauseRecording,
    resumeRecording,
    status,
    errorMessage
  } = useAudioRecorder()
  return (
    <div>
      <audio controls src={audioResult} />
      <p>
        Status : <b>{status}</b>
      </p>
      <p>
        Error Message : <b>{errorMessage}</b>
      </p>
      <div>
        <p>{new Date(timer * 1000).toISOString().substr(11, 8)}</p>
        <div>
          <button onClick={startRecording}>Start</button>
          <button onClick={stopRecording}>Stop</button>
          <button onClick={pauseRecording}>Pause</button>
          <button onClick={resumeRecording}>Resume</button>
        </div>
      </div>
    </div>
  )
}
```

## License

MIT © [LucasSilbernagel](https://github.com/LucasSilbernagel)
