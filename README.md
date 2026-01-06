# Building Frida-Core

This guide walks through the steps to build Frida-core for Android ARM64.

## Prerequisites

Ensure you have the necessary development tools installed on your macOS system.

## Build Steps

### 1. Find Code Signing Identity

First, locate your available code signing identities:

```bash
security find-identity -v -p codesigning
```

This will list all available code signing certificates. Find the one you want to use and note its identifier.

### 2. Export the Certificate ID

Set the `MACOS_CERTID` environment variable with your certificate identifier:

```bash
export MACOS_CERTID="<your-certificate-id>"
```

Replace `<your-certificate-id>` with the actual identifier from step 1.

### 3. Export Android NDK Root

Set the `ANDROID_NDK_ROOT` environment variable to your r25 NDK installation path:

```bash
export ANDROID_NDK_ROOT=/Users/'<abc>'/Library/Android/sdk/ndk/25.2.9519653
```

### 4. Configure for Android ARM64

Run the configure script targeting Android ARM64:

```bash
./configure --host=android-arm64
```

### 5. Build

Compile Frida-core using make:

```bash
make
```

This may take several minutes depending on your system.

## Output

Once the build completes successfully, the compiled frida-server binary will be located at:

```
build/server/frida-server
```

You can now use this binary on your Android ARM64 device.
