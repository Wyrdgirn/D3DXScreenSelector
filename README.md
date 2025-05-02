# D3DXScreenSelector

# Description

Enable the use of the --screen argument on some fullscreen apps and games. Allows you to select the screen on which the game will be displayed.

The Direct3D9 Wrapper library is based on the [Gist by shaunlebron](https://gist.github.com/shaunlebron/3854bf4eec5bec297907).

This, in addition, allows you to set the swap effect with` --swapmode` and the number of backbuffers with` --d3ddoublebuffer` and` --d3dtriplebuffer` too.

Only works with some fullscreen apps and games that use Direct3D9.

Games tested:

- Silent Hill 2 with Enhanced Edition mod (with `Run the game in DirectX 9` enabled and `Front buffer data capture method` set to `Use DirectX`)
- Castlevania Lords of Shadow
- Need for Speed Most Wanted (2005)
- Silent Hill 3 with enb d3d8to9 convertor
- Halo 1

This doesn't work with modern d3d9 games like:
- Castlevania Lords of Shadow 2
- Castlevania Lords of Shadow Mirror of Fate
- Dead or Alive 5 Last Round
- Dragon Ball Xenoverse
- Halo 2 (I don't know if it uses d3d9 anyway -.-;)

# Installation

Just put the `d3d9.dll` file in the same folder as the game executable.

This library uses the `d3d9.dll` original from the system folder. you can change the path using the argument ` --d3d9path`

# Compilation

Just use Visual Studio 2022 or later. You can try to compile with other versions and/or compilers, but you need to change the code a little bit. I don't know if it will work with other compilers, but I don't see why not.

# Usage

Make a shortcut to the game executable and add the following arguments (only what you need or all of them):

```
--screen=<screen number>
--swapmode=<swap effect> (can be copy, flip, discard, and overlay)
--d3ddoublebuffer for a double backbuffer or --d3dtriplebuffer for a triple backbuffer
--d3d9path=<path to d3d9.dll>
```

For example:

```
"C:\Program Files (x86)\Konami\Silent Hill 2\sh2pc.exe" --screen=1 --swapmode=copy --d3ddoublebuffer --d3d9path="C:\Program Files (x86)\Konami\Silent Hill 2\d3d9_orig.dll"
```

# Notes

- This library are not designed to work together with other wrappers, you can try setting the path to other wrappers using the `--d3d9path` argument , but I don't guarantee it will work!
- If you set the arguments more than once, the last one will be used. For example, if you set `--screen=1` and then `--screen=2`, the screen will be set to 2.
- The swap effect is not set by default, it uses the selected swap effect from the game.
- The backbuffer is not set by default, it uses the selected backbuffer from the game.
- The screen is not set by default, it uses the selected screen from the game. If you select a screen that is not available, it will use the default screen from the game.
- If you use the double or triple backbuffer, some swap effects can crash the game. Change --swapmode until you find one that works.
- This wrapper have problems with the Window of the game. The Window remains on the main screen and the game is displayed on the selected screen. This is a problem with the Direct3D9 API. Soon I will try hooking the CreateWindow and CreateWindowEx functions to try to make the window directly from the wrapper. If you know a better way to fix it, please let me know.
- This have functions to set the screen position that are made using AI support, but I don't know if they work, the window remains on the main screen, I just leave it just in case. I try other methods but they don't work. I will try to fix it in the future.
- This library is not perfect, it is a work in progress. If you find any bugs or have any suggestions, please let me know.
- Maybe (and just maybe) I port this to Direct3D8, but I prefer to wait to fix this library first.

# Acknowledgements

- [shaunlebron](https://gist.github.com/shaunlebron/3854bf4eec5bec297907) for the d3d9 wrapper code.
- [Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=6812) for the Direct3D9 API.
- [Microsoft Copilot](https://www.microsoft.com/en-us/microsoft-365/copilot) for help me with the GetMainWindowHandle and MoveWindowToSecondaryScreen functions... and this Readme :P.

# License

This project is only for personal use. All the code I don't wrote is under the license of the original authors. I don't take any responsibility for any damage this library may cause to your computer or your games. Use it at your own risk.

If you use this library in your project, please give credit to the original authors. If you want to use this library in a commercial project, please contact me first.

# Donations

If you want to support my work, you can donate me a coffee or a beer. I will appreciate it a lot. you can use my PayPal for that. this is not mandatory, but it will help me to keep working on this project and other projects in the future.

[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://paypal.me/DarkAyane?country.x=VE&locale.x=es_XC)

# The End... for now...

See ya! Wyrdgirn.
