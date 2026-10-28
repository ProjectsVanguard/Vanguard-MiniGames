# Vanguard MiniGames

A responsive mini-games hub by Projects Vanguard with desktop and Android packaging.

## Included
- Login and registration demo.
- Reaction, memory and 10-second click mini-games.
- Coins and local leaderboard.
- Friends list.
- Create custom click-challenge mini-games with a name, icon and coin reward.
- GitHub Actions workflow to build Windows EXE, Linux DEB/AppImage, macOS DMG and Android APK.

## Run
Requires Node.js 20+:
```bash
npm install
npm start
```

## Build desktop installers
Run the target command on the matching operating system:
```bash
npm run dist:win
npm run dist:linux
npm run dist:mac
```
Output is saved in `dist/`.

## Build Android APK
The workflow prepares the web assets and generates the Capacitor Android project automatically. For a local build:
```bash
mkdir -p web
cp index.html web/index.html
npx cap add android
npx cap sync android
cd android
./gradlew assembleDebug
```

## Publish a release
Push a tag such as `v1.0.0` to start the workflow:
```bash
git tag v1.0.0
git push origin v1.0.0
```
When all build jobs pass, the workflow publishes the EXE, DEB, AppImage, DMG and APK files on the GitHub Releases page. You can also run the workflow manually from the Actions tab to build downloadable artifacts (manual runs do not create a Release).

## Important authentication note
Login/registration currently works in **demo mode only**. Profiles and passwords are stored in local browser storage, so accounts are device-specific and this is not secure production authentication. Do not use a real/reused password. Before public launch, replace this demo with a server-backed authentication service and database. Friends and rankings are also local, not synchronized between players yet.

## License
MIT
