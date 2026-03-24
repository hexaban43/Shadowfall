# Shadowfall Windows Release Feed

This folder is the local staging area for launcher update artifacts.

## One-time setup

1. Copy `release-config.json.example` to `release-config.json`.
2. Set `manifestBaseUrl` to the public folder URL where you will host your update files.
3. Set the launcher `manifestUrl` to the matching `latest.json` URL.

Example:

```json
{
	"manifestBaseUrl": "https://hexaban43.github.io/Shadowfall/windows",
	"packageUrlTemplate": "https://github.com/hexaban43/Shadowfall/releases/download/v{version}/{packageName}",
	"manifestUrl": "https://hexaban43.github.io/Shadowfall/windows/latest.json"
}
```

Generated files go here:

- `latest.json`
- `Shadowfall-win64-<version>.zip`

Generate them with:

```powershell
powershell -ExecutionPolicy Bypass -File z:\Shadowfall\Codes\godot_shadowfall\tools\publish_release.ps1 -Version 0.2.0
```

After the script runs:

1. Upload `latest.json` to the public URL that matches `ManifestBaseUrl`.
2. Upload the zip file as a GitHub Release asset for tag `v<version>`.

## Easiest beginner option: GitHub Pages

If you do not already have hosting, the simplest path is:

1. Use your `hexaban43/Shadowfall` repo.
2. Enable GitHub Pages for the repo.
3. Upload `latest.json` to a `windows/` folder in the published branch.
4. Create a GitHub Release tagged like `v0.2.0`.
5. Upload `Shadowfall-win64-0.2.0.zip` as the release asset.

Example hosted files:

- `https://your-username.github.io/shadowfall/windows/latest.json`
- `https://github.com/your-username/shadowfall/releases/download/v0.2.0/Shadowfall-win64-0.2.0.zip`