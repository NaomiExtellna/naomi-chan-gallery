# Naomi-Chan™ Gallery Assets

Public image asset repository for the Naomi-Chan™ website gallery.

This repository is intentionally separate from the private application source repository. It contains approved public gallery photography uploaded through the Naomi-Chan™ staff Photo Library.

## Purpose

The Flask website uploads validated gallery images here and stores only their metadata and public raw URLs in Neon PostgreSQL.

```text
Staff Photo Library
        ↓
GitHub gallery asset repository
        ↓
raw.githubusercontent.com image URL
        ↓
Neon gallery_photos metadata
        ↓
https://naomi-chan.com/photos
```

## Repository layout

```text
images/
├── <generated-uuid>.jpg
├── <generated-uuid>.png
└── <generated-uuid>.webp
```

Uploaded filenames are generated automatically by the website. Original user-supplied filenames are not retained.

## Supported image formats

The website currently accepts:

- JPEG
- PNG
- WebP

The upload service validates the actual file signature before committing an image.

## Public access

This repository must remain **public** so the website can display assets through `raw.githubusercontent.com` without requiring authentication from visitors.

Anything committed here should be treated as publicly accessible, even when the corresponding Neon gallery record is marked as a Draft.

Do not store:

- private or embargoed photography;
- staff records;
- credentials or API tokens;
- `.env` files;
- database exports;
- application source code;
- personal information that is not approved for publication.

## Managed automatically

Images in `images/` are normally created and deleted by the Naomi-Chan™ website through the GitHub Contents API.

Manual changes are possible, but deleting or renaming an image by hand can break a gallery record whose `image_url` and `image_storage_key` still point to the old location.

## Related application

Website source repository:

```text
NaomiExtellna/naomi-chan-website
```

Gallery metadata table:

```text
public.gallery_photos
```

Public gallery route:

```text
/photos
```

Staff management routes:

```text
/staff/photos
/staff/photos/add
/staff/photos/<id>/edit
```

## Ownership

Naomi-Chan™ / Naomi Extellna

This repository is an operational media store for the Naomi-Chan™ website and is not intended as a general-purpose file archive.
