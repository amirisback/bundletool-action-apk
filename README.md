# BundleTool Action APK
[![Codacy Badge](https://app.codacy.com/project/badge/Grade/667085e10b6740fda8942b1a11e5b866)](https://www.codacy.com/gh/amirisback/bundletool-action-apk/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=amirisback/bundletool-action-apk&amp;utm_campaign=Badge_Grade)
[![tag badge](https://img.shields.io/github/v/tag/amirisback/bundletool-action-apk)](https://github.com/amirisback/bundletool-action-apk/tags)
[![license badge](https://img.shields.io/github/license/amirisback/bundletool-action-apk)](./LICENSE)

![Thumbnail](thumbnails.jpeg)

This action will help you convert your aab to apks file.

## Inputs

### `aabFile`

**Required:** The relative path in your project where your Android bundle file will be located

### `bundletoolVersion`

**Optional:** The version of bundletool to use. Defaults to `latest`

## Outputs
Output variables are set both locally and in environment variables.

### `apkPath`
The path to the single release apk file that have been signed with this action.

## Example usage

### Single APK

The output variable `signedReleaseFile` can be used in a release action.

```yaml
steps:
  - name: Convert aab to apk
    id: convert_aab
    uses: amirisback/bundletool-action-apk@v1.0.0
    with:
      aabFile: app/build/outputs/bundle/release/app-release.aab
      bundletoolVersion: '1.9.0'

  - uses: actions/upload-artifact@v3
    with:
      name: release-apk
      path: ${{ steps.convert_aab.outputs.apkPath }}
```