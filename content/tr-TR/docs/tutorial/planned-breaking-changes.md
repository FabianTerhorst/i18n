# Planlanmış API Değişimleri

Takip eden liste, Electron 3.0'da kaldırılacak API'leri içerir.

There is no timetable for when this release will occur but deprecation warnings will be added at least [one major version](electron-versioning.md#semver) beforehand.

## `Uygulama`

```js
// Kullanım Dışı
app.getAppMemoryInfo()
// İle değiştirin
app.getAppMetrics()
```

## `BrowserWindow`

```js
// Kullanım Dışı
let optionsA = {webPreferences: {blinkFeatures: ''}}
let windowA = new BrowserWindow(optionsA)
// İle Değiştirin
let optionsB = {webPreferences: {enableBlinkFeatures: ''}}
let windowB = new BrowserWindow(optionsB)
 
Context | Request Context

```

## `pano`

```js
// Deprecated
clipboard.readRtf()
// Replace with
clipboard.readRTF()

// Deprecated
clipboard.writeRtf()
// Replace with
clipboard.writeRTF()

// Deprecated
clipboard.readHtml()
// Replace with
clipboard.readHTML()

// Deprecated
clipboard.writeHtml()
// Replace with
clipboard.writeHTML()
```

## `crashReporter`

```js
// Kullanım Dışı
crashReporter.start({
  companyName: 'Crashly',
  submitURL: 'https://crash.server.com',
  autoSubmit: true
})
// İle Değiştirin
crashReporter.start({
  companyName: 'Crashly',
  submitURL: 'https://crash.server.com',
  uploadToServer: true
})
```

## `nativeImage`

```js
// Deprecated
nativeImage.createFromBuffer(buffer, 1.0)
// Replace with
nativeImage.createFromBuffer(buffer, {
  scaleFactor: 1.0
})
```

## `screen`

```js
// Deprecated
screen.getMenuBarHeight()
// Replace with
screen.getPrimaryDisplay().workArea
```

## `session`

```js
// Deprecated
ses.setCertificateVerifyProc(function (hostname, certificate, callback) {
  callback(true)
})
// Replace with
ses.setCertificateVerifyProc(function (request, callback) {
  callback(0)
})
```

## `Tray`

```js
// Deprecated
tray.setHighlightMode(true)
// Replace with
tray.setHighlightMode('on')

// Deprecated
tray.setHighlightMode(false)
// Replace with
tray.setHighlightMode('off')
```

## `webContents`

```js
// Deprecated
webContents.openDevTools({detach: true})
// Replace with
webContents.openDevTools({mode: 'detach'})
```

## `webFrame`

```js
// Deprecated
webFrame.registerURLSchemeAsSecure('app')
// Replace with
protocol.registerStandardSchemes(['app'], {secure: true})

// Deprecated
webFrame.registerURLSchemeAsPrivileged('app', {secure: true})
// Replace with
protocol.registerStandardSchemes(['app'], {secure: true})
```

## Node Başlıkları URLsi

Bu, bir `.npmrc` dosyasında `disturl` olarak veya yerel Node modülleri oluştururken `--dist-url` komut satırı işareti olarak belirtilen URL'dir.

Kullanımdan kaldırıldı: https://atom.io/download/atom-shell

Şununla değiştirildi: https://atom.io/download/electron

## `FIXME` yorumları

The `FIXME` string is used in code comments to denote things that should be fixed for the 3.0 release. See https://github.com/electron/electron/search?q=fixme