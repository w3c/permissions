# Extensibility

This document describes how the Permissions API can be used to express more complex permissions than the one currently
specified and how it should be used by other specifications.

## Permission description

```js
dictionary PermissionDescriptor {
  required PermissionName name;
};
```
```PermissionDescriptor``` is a dictionary that describes a permission. Its minimal content is a permission name but complex permissions can be described by more than a name. Such permissions should inherit from it and extend it.

## Simple permissions

```geolocation``` and ```notifications``` do not require more options for now. So their usage only require passing a ```PermissionDescriptor``` with a ```name```.

## Quota API

Quota API will need options because it is more granular than accepted/denied:
```js
dictionary QuotaPermissionDescriptor : PermissionDescriptor {
  required unsigned long long quota;
           StorageType type;
};
```

Checking ```quota``` permission would look like:
```js
navigator.permissions.query({name: 'quota', quota: '1024', type: 'persistent' }).then(function(status) {
  if (status.status == 'denied') {
    navigator.permissions.query({name:'quotar', quota: '512', type: 'persistent' }).then(ellipsis);
  }
});
```

## GetUserMedia

Capture has basically two permissions: audio and video. There are a couple of ways to design this.

### Have one permission with two booleans

```js
dictionary CapturePermissionDescriptor : PermissionDescriptor {
  required boolean audio;
  required boolean video;
};
```
But it might be odd if ```audio``` and ```video``` are both set to ```false```. Though, technically, the permission
should definitely be granted.

### Have an enum for the tri-state

```js
enum CapturePermissionType {
  "audio",
  "video",
  "audio-video"
}
dictionary CapturePermissionDescriptor : PermissionDescriptor {
  required CapturePermissionType type;
};
```

### Have two permissions

Simply ```capture-video``` and ```capture-audio```.

## Geolocation extended

The Geolocation specification defines a boolean called ```enableHighAccuracy```. Some user agents could have a
permissions behaviour depending on that value. We could imagine that the ```geolocation``` permission could be
extended to include this boolean in the future:
```js
dictionary GeolocationPermissionDescriptor : PermissionDescriptor {
  boolean enableHighAccurary = true;
};
```
