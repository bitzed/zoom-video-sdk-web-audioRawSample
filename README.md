# Zoom Video SDK audio raw data sample
This is a smallest sample that describes how to use the Zoom Video SDK Web with audio raw data.
For details, please visit [Zoom Video SDK for web](https://developers.zoom.us/docs/video-sdk/web/).

# How to use
1. You will need to populate the Video SDK client Key and secret in `.env` file. For details, visit [Get Video SDK credentials](https://developers.zoom.us/docs/video-sdk/developer-accounts/#get-video-sdk-credentials).

```
ZOOM_VSDK_KEY="YOUR VSDK KEY"
ZOOM_VSDK_SECRET="YOUR VSDK SECRET"
```

2. Then, run ```npm install``` to install required package.
3. ```node index.js``` to start.

# Change the voice pitch
You also can change the voice pitch by editing the following in `./public/js/pitch-shift-processor.js` ;

```javascript
  constructor(port, options) {
    super(port, options);

    this.bufferSize = 11025;
    this.buffer = new Float32Array(this.bufferSize);
    this.writePos = 0;
    this.readPos = 0.0;
    this.pitchRatio = options?.pitchRatio || 1.3;
    this.formantRatio = options?.formantRatio || 1.1;
    this.dryWet = options?.dryWet || 0.7;
    this.hpf = {
      prevIn: 0,
      prevOut: 0,
      alpha: 0.86
    };
  }
```

## Notes
You will need to run this on a SSL certified web server. If you run locally, you might need to use a CORS test Chrome extensions such as [Allow CORS: Access-Control-Allow-origin](https://chrome.google.com/webstore/detail/allow-cors-access-control/lhobafahddgcelffkeicbaginigeejlf/) before start.
