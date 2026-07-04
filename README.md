# Flutter SDK GitHub Action

The action installs the specified Flutter SDK version in the used runner.
Both Linux and macOS runners are supported.
By default, the latest stable release of the Flutter SDK is used.
The installed SDK is cached between runs, so subsequent runs of the same version skip the clone.


## Flutter SDK Versions

| Flutter SDK Version | Description | Default | Link |
| --- | --- | --- | --- |
| stable | Latest stable version of Flutter SDK | true | https://flutter.dev/docs/development/tools/sdk/releases |
| beta | Latest beta version of Flutter SDK | false | https://flutter.dev/docs/development/tools/sdk/releases |
| x.y.z | Exact version of Flutter SDK, like 3.44.4 | false | https://flutter.dev/docs/development/tools/sdk/releases |


## Inputs

| Name | Description | Default |
| --- | --- | --- |
| flutter-sdk-version | The Flutter SDK version to install (`stable`, `beta`, or an exact `x.y.z`) | `stable` |

## Outputs

| Name | Description |
| --- | --- |
| flutter-version | The resolved Flutter version reported by the installed SDK |


## Usage

Install Flutter SDK version 3.44.4 on macOS runner:

```yaml
on: [push]

jobs:
  main:
    runs-on: macos-latest
    steps:
      - uses: actions/checkout@v7
      - name: Install Flutter SDK
        uses: mobiledevops/flutter-sdk-action@v1
        with:
          flutter-sdk-version: 3.44.4
      - run: flutter --version
      - run: flutter doctor
      - run: flutter pub get
      - run: flutter test
      - run: flutter build ios --release --no-codesign 
```
