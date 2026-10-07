# Syncro — Android file transfer prototype

Syncro is a Kotlin and Jetpack Compose prototype for transferring a file between Android devices on a reachable local network. The current UI can select a file, send its bytes over a TCP socket, and receive files through a listener on port `8988`.

## Current implementation

- `MainActivity.kt` provides the file picker and send/receive screens.
- `LocalSender.kt` sends the selected file name and bytes to a receiver.
- `LocalReceiver.kt` listens for incoming files.
- `LocalDisovery.kt` contains local discovery code, but the send flow does not currently use it.
- `LocalCrypto.kt` contains ECDH and AES-GCM helpers, but the active send/receive path does **not** call them. Files sent by the current path are **not encrypted** by these helpers.

## Limitations

The receiver IP address is hard-coded in `MainActivity.kt`, and the Online option has no implementation yet. This is a learning prototype, not a finished secure file-sharing product. Do not use the current transfer path for sensitive files.

To explore the project, open it in Android Studio and inspect the local sender and receiver code before running it on devices you control.
