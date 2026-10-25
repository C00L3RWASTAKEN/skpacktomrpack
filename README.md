<div align="center">

# .skpack to .mrpack Converter

**Convert SKLauncher `.skpack` files into Modrinth `.mrpack` modpacks, right in your browser.**

[**Open the converter**](https://c00l3rwastaken.github.io/skpacktomrpack/) &nbsp;·&nbsp; [Report a problem](../../issues)


</div>

<!-- Add a screenshot of the page here:
<p align="center"><img src="screenshot.png" width="720" alt="The converter page"></p>
-->

## What it does

SKLauncher 4.0 can export an instance as an `.skpack`. Other launchers can't read that format. This tool turns it into an `.mrpack`, the format used by [Modrinth App](https://modrinth.com/app), [Prism Launcher](https://prismlauncher.org) and other launchers that import Modrinth packs.

Drop a file in, pick what to include, download the result. Nothing is uploaded anywhere.

## How to use it

1. Open the converter page.
2. Drop your `.skpack` file onto it.
3. Check the file list and options.
4. Click **Convert to .mrpack**, then download the file.
5. In your launcher, import the `.mrpack`. In Modrinth App that's **Add instance → Import from file**.

## What gets converted

| In the skpack | In the mrpack |
| --- | --- |
| `skpack.json` pack name, version | `modrinth.index.json` name and version |
| Minecraft version and loader (Fabric, Quilt, Forge, NeoForge) | `dependencies` entry for each |
| Mods and shaders hosted on Modrinth | Linked by download URL, with SHA-1 and SHA-512 hashes |
| Mods and shaders from CurseForge | Looked up on Modrinth by hash and linked if found, otherwise bundled from files you supply |
| Disabled files | Kept, with a `.disabled` suffix |
| `overrides/` (configs, shader settings) | Copied into the pack's `overrides/` |
| `overrides/saves/` worlds | Copied, and you can include or exclude each world |
| `overrides/screenshots/` | Copied, and you can include or exclude them |
| `icon.webp` | Offered as a separate download, since `.mrpack` has no icon field |

## Options

- **Look up files on Modrinth** finds Modrinth downloads for CurseForge files and sets each file's client/server support. It needs an internet connection and sends only file hashes to `api.modrinth.com`. Turn it off to stay fully offline.
- **Remove junk from overrides** drops crash logs, download logs and world-specific JEI history.
- **Worlds and screenshots** let you choose exactly which worlds and whether screenshots go into the pack.

## Files Modrinth can't host

`.mrpack` files can only link to approved download hosts, and CurseForge isn't one of them. If a CurseForge file can't be matched on Modrinth, the page lists it. Add the original file and it is bundled inside the pack, matched by its SHA-1 hash so the wrong file can't slip in. Anything left unmatched is skipped, and the log tells you which.

## Privacy

- The conversion runs entirely in your browser.
- Your pack, worlds and screenshots never leave your computer.
- The only network request is the optional Modrinth lookup, which sends file hashes and nothing else.

## Requirements

A recent browser with native compression support: Chrome or Edge, Firefox 113+, or Safari 16.4+. The page must be served over HTTPS (or opened locally), which GitHub Pages does by default.


## Limitations

- Built and tested against exported packs from SKLauncher 4.0.55 (skpack format version 1, Fabric, Minecraft 26.3). Other loaders and launcher versions follow the same format as far as I know, but haven't been tried.
- Large worlds are processed in memory, so very big packs may be slow.
- Worlds and screenshots belong to you. If you plan to publish the pack on Modrinth, untick them, since Modrinth may not accept them.

## Not affiliated

This is an unofficial community tool. It is not affiliated with or endorsed by SKLauncher or Modrinth.

## License

[MIT](https://github.com/C00L3RWASTAKEN/skpacktomrpack/blob/main/LICENSE).
