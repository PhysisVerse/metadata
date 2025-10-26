# Physis Ecosystem Metadata Repository

This repository serves as the **canonical source of metadata and digital assets** for all tokens, products, and ecosystem components within **Physis**.

## Purpose

The repository provides a single, version-controlled location for immutable metadata JSON files and associated media (icons, thumbnails, etc.) used across Solana SPL tokens, NFT collections, and integrated services.

Each directory within the repo corresponds to a unique Physis sub-project or token.

---

## Repository Structure

```
/phy/
  logo-256.v1.png
  metadata.v1.json
/syncral/
  logo-256.v1.png
  metadata.v1.json
/astralis/
  logo-256.v1.png
  metadata.v1.json
manifest.json
README.md
```

* **`/phy/`**, **`/syncral/`**, **`/astralis/`** — project-specific metadata folders.
* **`manifest.json`** — top-level registry mapping each token or asset to its latest metadata file.
* **`README.md`** — this documentation.

---

## Accessing Metadata

All assets are publicly accessible via the **jsDelivr CDN**, providing global caching and high availability:

```
https://cdn.jsdelivr.net/gh/physis/metadata@v1/phy/metadata.v1.json
https://cdn.jsdelivr.net/gh/physis/metadata@v1/phy/logo-256.v1.png
```

Replace `@v1` with the desired tag or commit SHA for immutable referencing.

---

## Versioning & Tagging

1. Upload or edit metadata files through the GitHub web interface.
2. Commit changes to the main branch.
3. Create a **new tag** (e.g., `v2`) from the GitHub *Releases* page.
4. Update on-chain metadata URIs to reference the new version tag:

   ```
   https://cdn.jsdelivr.net/gh/physis/metadata@v2/phy/metadata.v2.json
   ```

Older tags remain accessible for audit and historical reference.

---

## Update Workflow

1. Prepare new metadata and assets locally or via web UI.
2. Commit to the corresponding project folder.
3. Tag the repository with a version increment.
4. Verify CDN responses:

   ```bash
   curl -I --max-redirs 0 https://cdn.jsdelivr.net/gh/physis/metadata@v2/phy/metadata.v2.json
   ```
5. Confirm the `HTTP/2 200 OK` response (no redirects).

---

## Standards

* **File format:** JSON (UTF-8) following [Metaplex Token Metadata Standard](https://docs.metaplex.com/programs/token-metadata/overview)
* **Images:** PNG, 256×256 or 512×512, < 200 KB
* **Headers:** Served automatically by jsDelivr with proper `Content-Type` and CORS support.

---

## Manifest Example

```json
{
  "phy": "https://cdn.jsdelivr.net/gh/physis/metadata@v2/phy/metadata.v2.json",
  "syncral": "https://cdn.jsdelivr.net/gh/physis/metadata@v1/syncral/metadata.v1.json",
  "astralis": "https://cdn.jsdelivr.net/gh/physis/metadata@v1/astralis/metadata.v1.json"
}
```

---

## Governance

The repository is maintained by **Physis Labs** under the oversight of the **Physis DAO**. Any modifications must:

* Maintain backward compatibility for existing tags.
* Follow semantic versioning for metadata (`v1`, `v2`, `v3`, ...).
* Include clear commit messages describing the change.

---

## License

All metadata and associated assets are released under the **Physis Open Asset License (POAL)** — allowing open indexing and reference while maintaining project integrity.

---

Physis Labs © 2025
