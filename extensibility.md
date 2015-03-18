# Extensibility

This document describes how the Permissions API can be used to express more complex permissions than the one currently
specified and how it should be used by other specifications.

## Permission description

```js
enum PermissionName {
  "foo",
  "bar"
};
```
```PermissionName``` has an entry for each permission know to the API. It is recommended for APIs to use their
specification shorthand as a permission name. For the moment, the Permissions API is used as a registry to prevent
conflict.

```js
dictionary PermissionOptions {
};
```
```PermissionOptions``` is the property bag that will be used by permissions that need more than a name.

```js
interface Permission {
  PermissionName name;
  PermissionOptions options;
};
```
This is how a permission is represented.

## Simple permissions

The following permissions are currently described in the Permissions API and are considered simple permissions because 
they do not require options: ```geolocation```, ```notifications```, ```push-notifications``` and ```midi-sysex```.

## Quota API

Quota API will need options because it is more granular than accepted/denied:
```js
dictionary QuotaPermissionOptions : PermissionOptions {
  required unsigned long long quota;
           StorageType type;
};
```

Checking ```quota``` permission would look like:
```js
Permissions.query('quota', { quota: '1024', type: 'persistent' }).then(function(status) {
  if (status.status == 'denied') {
    Permissions.query('quota', { quota: '512', type: 'persistent' }).then(ellipsis);
  }
});
```

## GetUserMedia

Capture has basically two permissions: audio and video. There are a couple of ways to design this.

### Have one permission with two booleans

```js
dictionary CapturePermissionOptions : PermissionOptions {
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
dictionary CapturePermissionOptions : PermissionOptions {
  required CapturePermissionType type;
};
```

### Have two permissions

Simply ```capture-video``` and ```capture-audio```.

## Geolocation extended

TBD
