# pexels
Pexels REST client for Dart

## Usage

To use this library, add ```pexels``` as a dependency in your pubspec.yaml file.

## Getting Started

```dart
// import pexels
import "package:pexels/pexels.dart";

// create client instance
var client = PexelsClient('your_key_here');


// get a photo from ID
PexelsPhoto photo = await client.getPhoto(id);

// get a random photo
PexelsPhoto photo = await client.getPhoto();    // notice that the getPhoto method is called with no arguments.

// get the photo's url
String photoUrl = photo.sources['original'].link
// equivalent to:
String photoUrl = photo.get(ImageFormats.original);

// search photos
SearchResult<PexelsPhoto> result = await client.searchPhotos(query,collection: PexelsCollection.Popular,page: 1,resultsPerPage:15);
PexelsPhoto photo = result[0]; // get the first photo found.

// search portrait-only photos
SearchResult<PexelsPhoto> result = await client.searchPhotos(query,collection: PexelsCollection.Regular, orientation: PexelsPhotoOrientation.portait);
PexelsPhoto photo = result[0]; // get the first photo found.


// get a video from ID
PexelsVideo video = await client.getVideo(id);

// get a random video
PexelsVideo video = await client.getVideo();    // notice that the getVIdeo method is called with no arguments.

// get a video source url
String videoUrl = video.sources[0].link;
// equivalent to:
String videoUrl = video.get(0);

// search videos
SearchResult<PexelsVideo> result = await client.searchVideos(query,collection: PexelsCollection.Regular,page: 1,resultsPerPage:15);
PexelsVideo video = result[0]; // get the first video found.



// get Quota - bundles statistics about the API usage.
Quota quota = await client.getQuota();
```


## LICENSE
see LICENSE