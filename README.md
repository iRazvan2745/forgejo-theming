# Theming Forgejo
Make your forgejo instance better


> **WARNING**: CSS is fully ai generated


# Installation guide

### Docker
add this to the volumes

change the local path with whatever you want this is just my preffered way to do it as all my configs are in there
```yaml
    volumes:
      - /opt/forgejo/css/theme-rizz.css:/data/gitea/public/assets/css/theme-rizz.css
```

create the file `/opt/forgejo/css/theme-rizz.css` and add 

then add these 2 environment variables
```sh
  FORGEJO__ui__THEMES=gitea,arc-green,forgejo-dark,forgejo-light,forgejo-auto,rizz
  FORGEJO__ui__DEFAULT_THEME=rizz
```

Restart the container and select the `rizz` theme from the settings.
