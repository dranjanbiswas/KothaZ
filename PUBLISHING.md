# Publishing KothaZ

## One-click publishing

Windows 10 à¦ à¦à¦‡ file run à¦•à¦°à§à¦¨:

```bat
ONE_CLICK_UPLOAD_TO_GITHUB.bat
```

## What it does

- Generates GitHub documentation
- Initializes Git
- Creates/connects GitHub repository
- Pushes source code
- Pushes release tag `v1.1.0`
- Opens JitPack URL

## Manual commands

```bat
git init -b main
git config user.name "Dr. Anjan Biswas Kabbo"
git config user.email "dr.anjanbiswaskabbo2@gmail.com"
git add .
git commit -m "Release KothaZ v1.1.0"
git remote add origin https://github.com/dranjanbiswas/KothaZ.git
git push -u origin main
git tag v1.1.0
git push origin v1.1.0
```

## JitPack

Open:

```text
https://jitpack.io/#dranjanbiswas/KothaZ/v1.1.0
```

Click `Get it`.

## Final Gradle dependency

```gradle
implementation 'com.github.dranjanbiswas:KothaZ:v1.1.0'
```
