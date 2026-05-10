# Theming Forgejo

Make your Forgejo instance look better with small CSS modules.

> **Warning**: this CSS is AI-generated.

## Modules

The modules live in [`modules/`](https://github.com/irazvan2745/forgejo-theming/tree/main/modules).

### `mocha-theme.css`

Main Forgejo theme colors.

![Mocha theme preview](./preview/mocha-theme.png)

```css
@import url("https://raw.githubusercontent.com/irazvan2745/forgejo-theming/main/modules/mocha-theme.css");
```

### `syntax-highlighting.css`

Chroma code highlighting colors.

![Syntax highlighting preview](./preview/syntax-highlighting.png)

```css
@import url("https://raw.githubusercontent.com/irazvan2745/forgejo-theming/main/modules/syntax-highlighting.css");
```

### `material-icon.css`

Material-style repository file icons.

![Material icon preview](./preview/material-icon.png)

```css
@import url("https://raw.githubusercontent.com/irazvan2745/forgejo-theming/main/modules/material-icon.css");
```

## Install Latest Modules

Create the CSS file that Forgejo will load:

```sh
sudo mkdir -p /opt/forgejo/css
sudo nano /opt/forgejo/css/theme-rizz.css
```

Add the modules you want. These imports always use the latest files from the GitHub repo's `main` branch.

```css
@import url("https://raw.githubusercontent.com/irazvan2745/forgejo-theming/main/modules/mocha-theme.css");
@import url("https://raw.githubusercontent.com/irazvan2745/forgejo-theming/main/modules/syntax-highlighting.css");
@import url("https://raw.githubusercontent.com/irazvan2745/forgejo-theming/main/modules/material-icon.css");
```

Keep `mocha-theme.css` first if you use it as the base theme. Remove any imports for modules you do not want.

Example with only the theme and file icons:

```css
@import url("https://raw.githubusercontent.com/irazvan2745/forgejo-theming/main/modules/mocha-theme.css");
@import url("https://raw.githubusercontent.com/irazvan2745/forgejo-theming/main/modules/material-icon.css");
```

## Install From JSR

JSR serves package files by version, so use this when you want a pinned install instead of latest.

```css
@import url("https://jsr.io/@irazvan2745/forgejo-theming/<version>/modules/mocha-theme.css");
@import url("https://jsr.io/@irazvan2745/forgejo-theming/<version>/modules/syntax-highlighting.css");
@import url("https://jsr.io/@irazvan2745/forgejo-theming/<version>/modules/material-icon.css");
```

Replace `<version>` with the JSR version you want to pin.

## Docker Setup

Mount the CSS file into Forgejo:

```yaml
services:
  forgejo:
    volumes:
      - /opt/forgejo/css/theme-rizz.css:/data/gitea/public/assets/css/theme-rizz.css:ro
```

Add the theme to your Forgejo environment:

```sh
FORGEJO__ui__THEMES=gitea,arc-green,forgejo-dark,forgejo-light,forgejo-auto,rizz
FORGEJO__ui__DEFAULT_THEME=rizz
```

Restart Forgejo, then select the `rizz` theme in your user settings.

## Updating Modules

The GitHub imports automatically point at the latest files. Restart Forgejo or clear cached CSS if your instance does not pick up changes immediately.
