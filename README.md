# Adaptive HUD Brightness

This Better Than Wolves CE 3.0.0 addon dynamically adjusts the brightness of the Heads-Up Display (HUD) based on the light conditions around the player. Experience enhanced immersion and reduced eye strain as your interface adapts to your environment—dim in caves, bright in sunlight.

*"Darkness which may be felt."* – Exodus 10:21  
[wikiquote](https://en.wikiquote.org/wiki/Darkness)

-----

## Features

### ✨ Dynamic Brightness

* **Light-Aware HUD**: The HUD responds to the light level at the player's eye position, making low-light areas darker and bright areas fully visible.
* **Vanilla blocks and ambient light** influence HUD brightness naturally—torches, sunlight, and even moon phases affect how bright your interface appears.
* The effect is limited to the HUD; it does **not** affect world lighting or gameplay mechanics.
* Brightness changes are **smoothed across frames** to reduce abrupt jumps and flickering.

### 💻 Client-Side Only
* All effects and calculations occur on the **client side**.
* No changes to the server, world data, or other players' experiences.
* Perfect for multiplayer servers—install it yourself without affecting anyone else.

### 🕯️ Thoughtful Adjustments 
* Even in total darkness, a **minimum brightness threshold** ensures the HUD remains visible and usable.
* Brightening happens quickly (when entering light), while darkening is gradual (when entering darkness)—mimicking natural eye adaptation.

### 🌓 Moon Phase & Day/Night Awareness
* The addon accounts for **moon phases**, providing slightly more ambient light during a full moon and less during a new moon.
* Day/night cycles naturally affect HUD brightness, with smooth transitions at sunrise and sunset.

### 🎬 Bonus Use
* Could help in the **video editing process** if you need to brighten footage while keeping HUD elements visible in dark scenes.

-----

## Installation

1. Install **Better Than Wolves: Community Edition 3.0.0** + **Legacy Fabric** by following the instructions on the [BTW CE wiki](https://wiki.btwce.com/view/3.0.0_Beta).
2. Download the latest **Adaptive-HUD-Brightness-\<version\>.jar** from the [Releases page](https://github.com/BTW-Community/Adaptive_HUD_Brightness/releases).
3. Place the addon JAR file in your `.minecraft/mods/` folder.
4. Launch Minecraft. The HUD will now adapt its brightness automatically—no configuration needed!

-----

## Project Structure

```
src/main/
├── java/
│   ├── btw/community/abbyread/adaptivehud/
│   │   ├── AdaptiveHudBrightness.java        # Main mod entry point
│   │   └── BrightnessHelper.java             # Core brightness calculation logic
│   └── net/fabricmc/abbyread/mixin/
│       ├── FontRendererMixin.java            # Dims text rendering
│       ├── GuiIngameMixin.java               # Applies brightness to main HUD elements
│       ├── GuiScreenAccessor.java            # Accessor for GUI state
│       ├── MinecraftAccessor.java            # Accessor for Minecraft instance
│       ├── RenderBlocksMixin.java            # Adjusts item block rendering
│       └── RenderItemMixin.java              # Adjusts item icon rendering
└── resources/
    ├── assets/abbyread/icon.png              # Addon icon
    ├── fabric.mod.json                       # Mod metadata
    └── mixins.adaptive-hud-brightness.json   # Mixin configuration
```

-----

## Building from Source

**Requirements:**

* Java 17 or higher
* BTW CE 3.0.0 Intermediary Distribution (available in the Pinned section of `#learn-modding` on the [BTW CE Discord](https://discord.btwce.com/))

**Build Instructions:**

```bash
# Install BTW Intermediary
# Windows: Drag and drop the BTW Intermediary .zip onto install.bat
# Unix-like: ./install.sh <path-to-BTW-Intermediary.zip>

# Build the addon
./gradlew build

# Compiled output location:
# build/libs/Adaptive-HUD-Brightness-<version>.jar
```

-----

## Compatibility

* **BTW CE Version:** 3.0.0
* **Mod Loader:** Legacy Fabric (packaged with BTW CE)
* **Java:** 17 or higher

### Cross-Addon Compatibility

**Tested Compatible With:**
* ✅ [Dynamic Lights](https://github.com/BTW-Community/Dynamic-Lights-3) by [Hiracho](https://github.com/Hirachosan)
* ✅ [BTW-FreeLook](https://github.com/jeffinitup/btw-freelook) by [jeffinitup](https://github.com/jeffinitup)

**Potential Conflicts:**
* Addons that modify HUD rendering or GUI elements may conflict visually
* This addon exclusively modifies rendering classes using Mixin injections into `FontRenderer`, `GuiIngame`, `RenderBlocks`, and `RenderItem`
* Conflicts are unlikely unless another addon also patches these specific rendering methods

-----

## How It Works

The addon calculates HUD brightness based on:

1. **Block Light**: Light from torches, glowstone, lava, and other light-emitting blocks at the player's eye position
2. **Ambient Light**: Sunlight and moonlight, adjusted for time of day and moon phase
3. **Smooth Interpolation**: Brightness transitions are smoothed over time to prevent jarring changes
4. **Brightness Clamping**: A minimum brightness (10%) ensures the HUD never becomes completely invisible

Simple calculation occurs every frame on the client and affects:
* Item bar and hotbar
* Health, hunger, and armor indicators
* Item icons and text
* Crosshair and other HUD overlays

**What it does NOT affect:**
* World lighting or block brightness
* Menu screens (inventory, crafting, etc.)

-----

## Links

* [GitHub Repository](https://github.com/BTW-Community/Adaptive_HUD_Brightness)
* [BTW CE Wiki](https://wiki.btwce.com/)
* [BTW CE Discord](https://discord.btwce.com/)
* [Legacy Fabric Wiki](https://fabricmc.net/wiki/)
* [BTW Gradle Fabric Example](https://github.com/BTW-Community/BTW-gradle-fabric-example)

-----

## License

Released under the **0BSD** (BSD Zero-Clause) license.

You are completely free to use, copy, modify, and share it however you see fit.

-----

## Credits

**Created by Abigail Read**

**Better Than Wolves:** Created by *FlowerChild*, continued by the BTW Community

Special thanks to:
* The **Legacy Fabric team** for keeping classic modding alive
* The **BTW CE community** for documentation and support
* **Hiracho** for Dynamic Lights Addon
* **jeffinitup** for the Freelook Addon