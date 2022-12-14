# ๐ Release Helper

![](https://img.shields.io/github/workflow/status/actions-cool/release-helper/CI?style=flat-square)
[![](https://img.shields.io/badge/marketplace-release--helper-blueviolet?style=flat-square)](https://github.com/marketplace/actions/release-helper)
[![](https://img.shields.io/github/v/release/actions-cool/release-helper?style=flat-square&color=orange)](https://github.com/actions-cool/release-helper/releases)

๐ค A GitHub Action that help you publish release.

> Mainly used `antd`. Suggest [**changelog**](https://github.com/ant-design/ant-design/blob/master/CHANGELOG.en-US.md) use the same format.

## ๐ Usage

### Example

```yml
name: ๐ค Auto Make Release

on:
  create

jobs:
  release-helper:
    runs-on: ubuntu-latest
    steps:
      - name: make release
        if: github.event.ref_type == 'tag'
        uses: actions-cool/release-helper@v2
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          triger: 'tag'
          changelogs: 'CHANGELOG.en-US.md, CHANGELOG.zh-CN.md'
          branch: 'master'
```

### Inputs

| Name | Desc | Type | Required |
| -- | -- | -- | -- |
| token | GitHub Token | string | โ |
| triger | Triggering conditions | string | โ |
| changelogs | The file path | string | โ |
| branch | The file branch | string | โ |
| tag | Tag for branch. Check startsWith | string | โ |
| release | Whether release. Default `true` | boolean | โ |
| draft | Whether create a draft (unpublished) release. Default `false` | boolean | โ |
| prerelease | Whether to identify the release as a prerelease. Default `false` | boolean | โ |
| prerelease-filter | Version filter prerelease| string | โ |
| prerelease-notice | prerelease ๆฏๅฆๅๅธ้้้็ฅ๏ผ้ป่ฎคไธบ false | boolean | โ |
| dingding-token | ๅๅธ้้้็ฅไฝฟ็จ | string | โ |
| dingding-msg | ๅๅธ้้ๅๅฎน๏ผไป changelogs ไธญ้ไธไธช | string | โ |
| dingding-delay-minute | ๅๅธ้้ๅๅฎนๅปถ่ฟ๏ผๅไฝๅ้ | string | โ |
| msg-title | ้้ๅๅฎนๆ ้ข่ชๅฎไน | string | โ |
| msg-poster | ้้ๅๅฎนๆตทๆฅ๏ผไผ ๅฅๅพ็ url | string | โ |
| msg-head | ้้ๅๅฎนไธป้ขๅ็ฝฎ่ชๅฎไน | string | โ |
| msg-footer | ้้ๅๅฎนไธป้ขๅ็ฝฎ่ชๅฎไน | string | โ |
| prettier | ้้ๅๅฎน็พๅ | boolean | โ |
| dingding-ignore | DingTalk ignore when version contain | string | โ |

- [้้็พค่ชๅฎไนๆบๅจไบบๆฅๅฅ](https://developers.dingtalk.com/document/robots/custom-robot-access)
- ็ฑไบ้้ๅฏนไบ็บงๅฑ็บงๅฑ็คบไธๅฅฝ๏ผ่ฟ้ๅฏ่ฎพ็ฝฎ prettier ๅผๅฏไบบไธบ็พๅ
- msg ่ชๅฎไนๆฏๆ 2 ไธชๆฟๆข
  - `{{v}}` -> ๅทไฝ็ๆฌ
  - `{{url}}` -> ๅๅธ้พๆฅ
  - ไพๅฆ๏ผ`msg-footer: '> footer: version is {{v}} url is [url]({{url}})'`
- ไฝ ๅฏไปฅ่ฎพ็ฝฎๅคไธช dingding-token
  - `dingding-token: ${{ secrets.TOKEN1 }} ${{ secrets.TOKEN2 }}`
- delay ๅ่ซ่ฎพ็ฝฎ่ฟๅคง๏ผๆ่ฎฐๅพ CI ่ถ่ฟๅ ไธชๅฐๆถ่ชๅจ่ฟๆ

### Workflow

- `git tag x.x.x`
- `git push origin x.x.x:x.x.x`
- New tag triger action
- Auto release with changelog

## โก Feedback

You are very welcome to try it out and put forward your comments. You can use the following methods:

- Report bugs or consult with [Issue](https://github.com/actions-cool/release-helper/issues)
- Submit [Pull Request](https://github.com/actions-cool/release-helper/pulls) to improve the code of `release-helper`

ไนๆฌข่ฟๅ ๅฅ ้้ไบคๆต็พค

![](https://github.com/actions-cool/resources/blob/main/dingding.jpeg?raw=true)

## LICENSE

[MIT](./LICENSE)
