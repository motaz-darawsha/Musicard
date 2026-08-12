<div align="center">

<img src="https://raw.githubusercontent.com/kunalkandepatil/.github/refs/heads/main/assets/musicard/banner.svg" alt="musicard banner" />
<br>
<br>


# **˗ˏˋ musicard ´ˎ˗**
A **powerful** canvas-based library to generate stunning, highly customizable music cards with modern themes and rich features.

[![NPM Version](https://img.shields.io/npm/v/musicard?style=flat-square&color=%23FF4C28)](https://www.npmjs.com/package/musicard)
[![NPM Downloads](https://img.shields.io/npm/dw/musicard?style=flat-square&color=%23FF4C28)](https://www.npmjs.com/package/musicard)
[![NPM License](https://img.shields.io/npm/l/musicard?style=flat-square&color=%23FF4C28)](https://github.com/unburn/musicard/blob/main/LICENSE)
[![GitHub Repo stars](https://img.shields.io/github/stars/unburn/musicard?style=flat-square&color=%23FF4C28)](https://github.com/unburn/musicard)

<br>

<img src="https://raw.githubusercontent.com/kunalkandepatil/.github/refs/heads/main/assets/musicard/features.svg" alt="musicard features" />

<br>

</div>


## 📄 Documentation 
### ╰┈1️⃣ Usage
```bash
npm install musicard
```
```js
import { initializeFonts, Bloom } from 'musicard';
import fs from 'node:fs';

(async () => {
    initializeFonts();

    const musicard = await Bloom({
        trackName: "Blinding Lights",
        artistName: "The Weeknd",
        albumArt: "", // Image Path/URL
        isExplicit: true,
        timeAdjust: {
            timeStart: "0:00",
            timeEnd: "2:54",
        },
        progressBar: 10,
        volumeBar: 70,
    });

    fs.writeFileSync('example.png', musicard);
    console.log('✅-> example.png');
})();
```

### Event card types

Every theme accepts an optional `type`. Omitting it, or using `"nowPlaying"`, preserves the existing card output.

| `type` | Card contents |
|---|---|
| `"nowPlaying"` | The existing time and progress layout. This is the default. |
| `"start"` | Hides the progress bar and displays a concise `STARTED` indicator. |
| `"add"` | Hides the progress bar and uses the available space for queue metadata. |

```js
const card = await Bloom({
    type: "add",
    trackName: "Blinding Lights",
    artistName: "The Weeknd",
    albumArt: "https://example.com/album-art.png",
    fallbackArt: "https://example.com/fallback.png",
    likes: 1200,
    views: 54000,
    position: 3,
});
```

For `"add"` cards, `likes`, `views`, and `position` are optional. If no metadata is provided, the card shows a neutral `Queued for playback` message. The same `type` option is available in `Bloom`, `Calm`, `Drift`, `Ease`, `Haze`, and `Melt`.

Here's how you can use `musicard` in a **Discord** bot to generate and send a music card image:
```js
const { initializeFonts, Bloom } = require("musicard");
const fs = require("fs")

await initializeFonts();
const musicard = await Bloom({...})

...

return message.channel.send({
    files: [{
        attachment: musicard
    }]
})
```

<p align="center">≪ ◦ ✦ ◦ ≫</p>

### ╰┈2️⃣ Structure
![musicard structure](https://raw.githubusercontent.com/kunalkandepatil/.github/refs/heads/main/assets/musicard/theme_structure.png)

<p align="center">≪ ◦ ✦ ◦ ≫</p>

### ╰┈3️⃣ Themes
![bloom](https://raw.githubusercontent.com/kunalkandepatil/.github/refs/heads/main/assets/musicard/bloom_theme.png)
![melt](https://raw.githubusercontent.com/kunalkandepatil/.github/refs/heads/main/assets/musicard/melt_theme.png)
![haze](https://raw.githubusercontent.com/kunalkandepatil/.github/refs/heads/main/assets/musicard/haze_theme.png)
![ease](https://raw.githubusercontent.com/kunalkandepatil/.github/refs/heads/main/assets/musicard/ease_theme.png)
![drift](https://raw.githubusercontent.com/kunalkandepatil/.github/refs/heads/main/assets/musicard/drift_theme.png)
![calm](https://raw.githubusercontent.com/kunalkandepatil/.github/refs/heads/main/assets/musicard/calm_theme.png)

<p align="center">≪ ◦ ✦ ◦ ≫</p>

### ╰┈4️⃣ Customize
You now have the **ability** to completely personalize your music card, such as:

1. Customize Background
```js
backgroundColor: "white"
```

2. Customize Text
```js
styleConfig: {
    trackStyle: {
        textColor: "black",
        textGlow: true,
        textItalic: true
    }
}
```

3. Customize Progress Bar
```js
styleConfig: {
    progressBarStyle: {
        barColor: "#000000",
        barColorDuo: true
    }
}
```

4. Custom Font support
```js
import { registerFont } from 'musicard';
registerFont('MyFont.ttf', 'MyFont');
```

> ⚠️ Note: To use custom fonts, create a `Fonts` folder in your project's root directory and place your font files (e.g., .ttf, .otf) inside it.

<p align="center">≪ ◦ ✦ ◦ ≫</p>

### ╰┈5️⃣ Examples
1. To see all **font names** currently registered and available for use:
```js
import { GlobalFonts } from 'musicard';
console.log(GlobalFonts); // Prints all registered font names
```

## 🎧 Support Server
<a href="https://discord.gg/W8wTjESM3t"><img src="https://raw.githubusercontent.com/kunalkandepatil/.github/refs/heads/main/assets/discord.svg" alt="support server" /></a>