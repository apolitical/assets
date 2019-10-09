# assets
Static assets shared across apolitical sites

- Fonts - Fonts that we don't want to host with google
- Images - e.g profile images from most_influential lists
- Logos - Apolitical and other company Logos
- SVGs - Any non-logo/texture svg
- Textures - background elements for web pages

# Development processes
**Creating a new version of an existing list page**
see: [frontends/lists/README.md](https://gitlab.com/apolitical/frontends/lists/blob/master/README.md)

# Troubleshooting

1. Check that Cloudflare is not caching (leave it to GitHub)
2. Enforce HTTPS
3. Make a change to the repo and push it

# Troubleshooting Lists

- copy & paste your json into https://jsonlint.com/ and press validate to see if you have valid json (it will highlight where it is invalid)
- if you are unsure about what is making the json invalid ask an engineer