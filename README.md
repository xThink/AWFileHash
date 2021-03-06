# AWFileHash

[![CI Status](https://travis-ci.org/leetal/AWFileHash.svg?branch=master)](https://travis-ci.org/leetal/AWFileHash)
[![Version](https://img.shields.io/cocoapods/v/AWFileHash.svg?style=flat)](http://cocoadocs.org/docsets/AWFileHash)
[![License](https://img.shields.io/cocoapods/l/AWFileHash.svg?style=flat)](http://cocoadocs.org/docsets/AWFileHash)
[![Platform](https://img.shields.io/cocoapods/p/AWFileHash.svg?style=flat)](http://cocoadocs.org/docsets/AWFileHash)

A security library that supports md5, sha1 and sha512 hashes, as well as CRC32b checksums. Performs all calculations chunked to reduce memory impact (does not apply to PHAsset as of now).

Returns a hex of the result.

## Requirements

iOS5+ is required. If using cocoapods or Swift, min version in podfile/build is iOS8. For PHAsset support iOS8+ is required.

## Usage/Examples
#### Swift
```swift
import AWFileHash
...
...
let data:NSData = NSData(data: "AWFileHash", length: 10)
let hash = AWFileHash.md5HashOfData(data)
print(hash)
```

#### Objective-C
Make sure to include AWFileHash.h where you want to use the lib.
```objectivec
// Filepath (file accessible on disk)
NSString *_filePath = ...
NSString *md5 = [AWFileHash md5HashOfFileAtPath:_filePath]

// NSData
NSData *_data = [NSData dataWithBytes:"AWFileHash" length:10];
NSString *md5 = [AWFileHash md5HashOfData:_data];

// ALAssetRepresentation
ALAsset *_asset = ...
ALAssetRepresentation *_assetRep = [_asset defaultRepresentation];
NSString *md5 = [AWFileHash md5HashOfALAssetRepresentation:_assetRep];
...
```

For SHA1, SHA512 or CRC32b  support, just replace the "md5" in the names to "sha1", "sha512" or "crc32" respectively.

## Installation
### Cocoapods
AWFileHash is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

    pod "AWFileHash"

### Manual
Download the .zip, unpack it and draw the files "AWFileHash.{m,h}" into XCode. Make sure to add them to your target bundle also.

## TODO

* Add support for PHAsset (need to find a way to stream bytes to AWFileHash)
* Add md5 categories for NSString & NSData
* Add proper documentation
* Add more tests that conform to the standards

## Definitions

Specifications: 
* MD5: [http://www.ietf.org/rfc/rfc1321.txt]
* SHA1 & SHA512: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf] 

## Author

Alexander Widerberg, widerbergaren [at] gmail.com

## License

AWFileHash is available under the MIT license. See the LICENSE file for more info.
