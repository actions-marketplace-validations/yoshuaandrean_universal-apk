# Universal APK Builder Action
![Action Build](https://github.com/skywall/universal-apk-builder/workflows/Action%20Build/badge.svg?branch=master)

This action converts given `*.aab` file to universal `*.apk` file. This file includes all 
dynamic modules.

## Inputs

### `aab_path`

**Required** Path to input `*.aab` file

### `output_dir`

**Optional** Path to directory where outputs are stored

Default: `output`

### `keystore_path`

**Required** Path to keystore file (`*.jks`)

### `keystore_password`

**Required & Sensitive** Keystore password

### `keystore_alias`

**Required & Sensitive** Keystore alias

### `keystore_alias_password`

**Required & Sensitive** Keystore alias password

## Outputs

### `universal_apk_path`

Path to final universal APK

## Example usage

```
- name: Build Universal APK
  uses: skywall/universal-apk-builder@v1.0.1
  with:
    aab_path: "/path/to/file.aab"
    keystore_path: "/path/to/keystore.jks"
    keystore_password: ${{secrets.KEYSTORE_PASSWORD}}
    keystore_alias: ${{secrets.KEYSTORE_ALIAS}}
    keystore_alias_password: ${{secrets.KEYSTORE_PASSWORD}}
- name: Do something with Universal APK
  with:
    apk_path: ${{env.UNIVERSAL_APK_PATH}}
```

## How to test locally

Use [Act](https://github.com/nektos/act).

```bash
$> brew install nektos/tap/act
$> act -j test-local -b
```
