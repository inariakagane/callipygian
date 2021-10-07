# callipygian

Static asset management system

## Aspirations

Currently a bit messy, but captures the activities I'm currently doing.

```json
...
[
  {
    "target": "face.png",
    "upload": "private",
    "uploadOriginal": true,
    "destination": "s3://bucket/public/assets/$folder/",
    "operations": {
      "resize": {
        "sizes": ["32x32", "64x64", "128x128"],
        "affix": ".$xx$y",
        "upload": false,
        "operations": {
          "compress": {
            "affix": ".png8",
            "upload": "public"
          }
        }
      }
    }
  },
  {
    "target": "video.mp4",
    "uploadOriginal": true,
    "upload": "private",
    "destination": "s3://bucket/public/assets/$folder/",
    "operations": {
      "ffmpeg": {
        "crop": "1080:1080",
        "scale": "512:512",
        "audio": false,
        "output": "webm",
        "quality": "1M",
        "upload": "public"
      },
      "snapshot": {
        "timestamp": "$middle",
        "crop": "1080:1080",
        "affix": "-preview",
        "upload": false,
        "operations": {
          "resize": {
            "sizes": ["128x128", "512x512"],
            "affix": ".$xx$y",
            "upload": false,
            "operations": {
              "compress": {
                "affix": ".png8",
                "upload": "public"
              }
            }
          }
        }
      }
    }
  }
]
...
```
