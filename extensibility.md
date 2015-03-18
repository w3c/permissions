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

TBD

## Fullscreen

TBD

## GetUserMedia

TBD

## Geolocation extended

TBD
