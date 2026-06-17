# Start Here: Windows 10 One-Click Upload Guide

à¦à¦‡ project folder à¦à¦° à¦­à¦¿à¦¤à¦°à§‡ à¦¸à¦¬ ready à¦†à¦›à§‡à¥¤ à¦†à¦ªà¦¨à¦¾à¦° à¦•à¦¾à¦œ à¦¶à§à¦§à§ à¦à¦•à¦¬à¦¾à¦° BAT file run à¦•à¦°à¦¾à¥¤

## à¦•à§€ à¦¹à¦¬à§‡ automatically

`ONE_CLICK_UPLOAD_TO_GITHUB.bat` run à¦•à¦°à¦²à§‡ script automatically:

1. Git check à¦•à¦°à¦¬à§‡
2. GitHub CLI check à¦•à¦°à¦¬à§‡
3. à¦¦à¦°à¦•à¦¾à¦° à¦¹à¦²à§‡ GitHub login à¦•à¦°à¦¾à¦¬à§‡
4. README.md à¦¤à§ˆà¦°à¦¿/update à¦•à¦°à¦¬à§‡
5. Java guide à¦¤à§ˆà¦°à¦¿/update à¦•à¦°à¦¬à§‡
6. Kotlin guide à¦¤à§ˆà¦°à¦¿/update à¦•à¦°à¦¬à§‡
7. Gradle implementation guide à¦¤à§ˆà¦°à¦¿/update à¦•à¦°à¦¬à§‡
8. Publishing guide à¦¤à§ˆà¦°à¦¿/update à¦•à¦°à¦¬à§‡
9. Git repository initialize à¦•à¦°à¦¬à§‡
10. GitHub repository create/connect à¦•à¦°à¦¬à§‡: `dranjanbiswas/KothaZ`
11. à¦¸à¦¬ file commit à¦•à¦°à¦¬à§‡
12. `main` branch GitHub à¦ push à¦•à¦°à¦¬à§‡
13. `v1.1.0` tag create/push à¦•à¦°à¦¬à§‡
14. GitHub Release create à¦•à¦°à¦¾à¦° à¦šà§‡à¦·à§à¦Ÿà¦¾ à¦•à¦°à¦¬à§‡
15. JitPack page open à¦•à¦°à¦¬à§‡

## à¦†à¦ªà¦¨à¦¾à¦° Windows 10 à¦ à¦¯à¦¾ à¦²à¦¾à¦—à¦¬à§‡

- Git for Windows
- GitHub CLI
- Android Studio later testing à¦à¦° à¦œà¦¨à§à¦¯

Script à¦à¦—à§à¦²à§‹ à¦¨à¦¾ à¦ªà§‡à¦²à§‡ winget à¦¦à¦¿à§Ÿà§‡ install à¦•à¦°à¦¾à¦° à¦šà§‡à¦·à§à¦Ÿà¦¾ à¦•à¦°à¦¬à§‡à¥¤ winget à¦¨à¦¾ à¦¥à¦¾à¦•à¦²à§‡ install link open à¦•à¦°à¦¬à§‡à¥¤

## Run à¦•à¦°à¦¾à¦° à¦¨à¦¿à§Ÿà¦®

1. ZIP extract à¦•à¦°à§à¦¨
2. Folder open à¦•à¦°à§à¦¨
3. `ONE_CLICK_UPLOAD_TO_GITHUB.bat` double click à¦•à¦°à§à¦¨
4. First time login à¦šà¦¾à¦‡à¦²à§‡ browser à¦¥à§‡à¦•à§‡ GitHub authorize à¦•à¦°à§à¦¨
5. Script à¦¶à§‡à¦· à¦¹à¦²à§‡ JitPack page open à¦¹à¦¬à§‡
6. JitPack à¦ `Get it` à¦šà¦¾à¦ªà§à¦¨

## GitHub username

```text
dranjanbiswas
```

## Repository name

```text
KothaZ
```

## Final library dependency

```gradle
implementation 'com.github.dranjanbiswas:KothaZ:v1.1.0'
```

## à¦¯à¦¦à¦¿ push error à¦†à¦¸à§‡

à¦¸à¦¬à¦šà§‡à§Ÿà§‡ common à¦•à¦¾à¦°à¦£:

- GitHub login à¦¹à§Ÿà¦¨à¦¿
- GitHub CLI install à¦¹à§Ÿà¦¨à¦¿
- Internet connection problem
- à¦à¦•à¦‡ à¦¨à¦¾à¦®à§‡ repo à¦†à¦—à§‡ à¦¥à§‡à¦•à§‡ à¦†à¦›à§‡ à¦•à¦¿à¦¨à§à¦¤à§ permission à¦¨à§‡à¦‡

Fix:

```bat
gh auth login
```

à¦¤à¦¾à¦°à¦ªà¦° à¦†à¦¬à¦¾à¦°:

```bat
ONE_CLICK_UPLOAD_TO_GITHUB.bat
```
