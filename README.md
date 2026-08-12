# Unity Game Live Translation Tool on Winlator

A tool for live-translating Unity games running on Android through Winlator, using BepInEx and AutoTranslator.

# README Vietnamese
[README Vietnamese](README_vi.md)

# BepInEx

BepInEx is a plugin / modding framework for Unity Mono, IL2CPP and .NET framework games (XNA, FNA, MonoGame, etc.)

(Currently only Unity Mono has stable releases)

#### Platform compatibility chart

|              | Windows | OSX  | Linux | ARM |
|--------------|---------|------|-------|-----|
| Unity Mono   | ✔️      | ✔️  | ✔️    | N/A |
| Unity IL2CPP | ✔️      | ❌   | ✔     | ❌  |
| .NET / XNA   | ✔️      | Mono | Mono  | N/A |

A more comprehensive comparison list of features and compatibility is available at https://bepis.io/unity.html


## ✨ Features

- 🔄 Live in-game text translation while the game is running
- 🌐 Supports Google Translate V2 as translation endpoint
- 📱 Runs on Android via Winlator (Wine-based Windows emulator)
- 🔧 Easy configuration through `AutoTranslatorConfig.ini`
- 🗂️ No root required

---

## 📦 Requirements

- **Android Device**: Android 8.0+
- **Winlator** installed
- **BepInEx** files downloaded and placed in the game folder
- **XUnity.AutoTranslator** plugin placed in BepInEx plugins folder — Note: Already bundled, no extra steps needed.
- Internet access for translation API calls

---

## ⚙️ Setup on Winlator

### Step 1 — Configure the Container

Tap the **+** button near the Container section, then tap the checkmark to create it.

Tap the **three-dot menu** → select **Edit**.

### Step 2 — Set Environment Variable

Go to the **Environment** tab and add a new variable:

| Name | Value |
|------|-------|
| `WINEDLLOVERRIDES` | `winhttp=n,b` |

> This tells Wine to use the native `winhttp.dll` before the built-in one, which is required for BepInEx to inject correctly.

How to add: tap **Add** → enter the name and value above → tap **OK**.

### Step 3 — Add winhttp via Winecfg

Inside the container, open **Wine Configuration** → go to the **Libraries** tab.

1. In the **New override for library** field, type `winhttp`
2. Tap **Add** (arrow ①)
3. Confirm `winhttp (native, builtin)` appears in the list
4. Tap **Apply** (arrow ①) then **OK** (arrow ②)

### Step 4 — Configure AutoTranslator

Run the game once so BepInEx generates the config file, then edit:

```
BepInEx/config/AutoTranslatorConfig.ini
```

Set it up as follows:

```ini
[Service]
Endpoint=GoogleTranslateV2
FallbackEndpoint=

[General]
Language=vi
FromLanguage=en
```

> ⚠️ The config file is only created **after running the game at least once** with BepInEx installed.

- `Language` — target language code (e.g. `vi` for Vietnamese, `zh` for Chinese)
- `FromLanguage` — source language of the game (e.g. `en` for English, `ja` for Japanese)

---

## 🚀 Usage — The steps above already cover everything, you can skip this section

1. Install Winlator and create a container for your game.
2. Copy BepInEx into the game folder inside the container.
3. Set `WINEDLLOVERRIDES=winhttp=n,b` in the container's environment variables.
4. Add `winhttp` as a native DLL override in Winecfg.
5. Run the game once to let BepInEx generate config files.
6. Edit `BepInEx/config/AutoTranslatorConfig.ini` as shown above.
7. Run the game again — text will be translated automatically.

---

## 🤝 Contributing

1. Fork this repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## ⚠️ Disclaimer

1. **Legal**: For educational and research purposes only. Please support official game releases.
2. **Compatibility**: Not all Unity games are compatible with BepInEx or AutoTranslator.
3. **Backup**: Always back up your game files before making any changes.
4. **API Limits**: Google Translate has rate limits; excessive use may result in temporary blocks.

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 👥 Developer Info

- **Developer**: chiuaquang
- **Telegram**: [@dexbillava](https://t.me/dexbillava)
- **BepInEx**: [BepInEx](https://github.com/BepInEx/BepInEx)
- **Translation Plugin**: [XUnity.AutoTranslator](https://github.com/bbepis/XUnity.AutoTranslator)
- **Issue Tracker**: [GitHub Issues](https://github.com/chiuaquang/TrUnity/issues)

---

## 🌟 Support

If this tool has been helpful to you, please:

- ⭐ Star this project
- 🐛 Submit an Issue to report problems
- 💬 Join the discussion

---

## Note

- This guide is specifically for running **Unity Windows games** on Android through **Winlator**.
- BepInEx and AutoTranslator are third-party tools — refer to their own documentation for advanced configuration.
- If translation does not work, double-check the `WINEDLLOVERRIDES` environment variable and the `winhttp` DLL override in Winecfg.
