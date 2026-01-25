# Zilla 

Zilla - is a minimalist web player that works completely without subscriptions or hidden fees with offline!<br/>

Go to zilla: https://reversedir.github.io/zila/index.html

How do I go offline? <br/>
1. Open Zilla in your browser
2. Go to Settings -> Go to local
3. Approximate size (~1 GB, most of it MP3)
4. Enjoy music anytime, even without internet access

Hmmm? <br/>
1. For those who want to listen to music without monthly payments
2. For travelers and those with unstable internet
3. For minimalists who value simple and functional solutions
4. Completely anonymous: no login, email, or phone number required. All data is stored and processed exclusively on the client side

How clone it project? (it's not easy) <br/>
1. Download 100-15000 mp3 (with tag: artist, title, genre, cover image)
2. Open local add.html or goto `/zila/add.html`
3. Select all mp3 files, you get audio.zip
4. Throw all .jpg and .mp3 files and audio.js in /audio folder
5. Run index.html

Advance info .mp3 to .opus with use ffmpeg and .ps1 (powershell script) <br />
```bash
$currentDirectory = $PWD.Path
$outputRoot = Join-Path $currentDirectory "render"
if (-not (Test-Path $outputRoot)) { New-Item -ItemType Directory -Path $outputRoot | Out-Null }
$oldvids = Get-ChildItem -Include *.mp3 -Recurse
foreach ($vid in $oldvids) {
  $newvid1 = Join-Path $outputRoot ([io.path]::ChangeExtension($vid.Name, 'opus'))
  ffmpeg -i $vid.FullName -c:a libopus -b:a 48k $newvid1
  $oldvid = ($vid.FullName).SubString($currentDirectory.Length + 1)
}
```
