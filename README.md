# Flutter SDK GitHub Action

The action installs the specified Flutter SDK version in the used runner.
Both Linux and macOS runners are supported.
By default, the latest stable release of the Flutter SDK is used.


## Flutter SDK Versionen

| Flutter SDK Version | Description | Default | Link |
| --- | --- | --- | --- |
| stable | Latest stable version of Flutter SDK | true | https://flutter.dev/docs/development/tools/sdk/releases |
| beta | Latest beta version of Flutter SDK | false | https://flutter.dev/docs/development/tools/sdk/releases |
| x.y.z | Exact version of Flutter SDK, like 3.7.7 | false | https://flutter.dev/docs/development/tools/sdk/releases |


## Usage

Install Flutter SDK version 3.7.7 on macOS runner:

```yaml
on: [push]

jobs:
  main:
    runs-on: macos-latest
    steps:
      - uses: actions/checkout@v3
      - name: Install Flutter SDK
        uses: mobiledevops/flutter-sdk-action@v1
        with:
          flutter-sdk-version: 3.7.7
      - run: flutter --version
      - run: flutter doctor
      - run: flutter pub get
      - run: flutter test
      - run: flutter build ios --release --no-codesign 
```
