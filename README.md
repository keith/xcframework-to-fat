This is a CLI to create a old style fat framework from a `xcframework`
bundle if you don't need support for Apple Silicon.

# Usage:

This command will create `Foo.framework` bundle with a `x86_64` iOS
Simulator slice and an `arm64` iOS device slice.

```sh
./xcframework-to-fat path/to/Foo.xcframework path/to/output x86_64-apple-ios-simulator arm64-apple-ios
```

See `./xcframework-to-fat --help` for more info.

## Notes

- You cannot use this in the case you actually need multiple
  architectures that support different platforms, in that case you must
  use xcframeworks. This only exists for the case where you don't need
  that, and maybe your tooling doesn't support xcframeworks yet
- Currently this tool isn't smart about resources that differ for device
  or simulator, when possible it copies the resources from the framework
  targeting device builds without diffing them
- Since binaries are changed through this transformations, any
  code signatures they previously had are removed
