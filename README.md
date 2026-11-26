# AI Character Reference and Composition Workbench - English Edition (3-in-1)

> **Pose library (1,439 mannequin references + 1,439 depth maps) + Costume library (3,224 sets: Gia realistic 1,407 + Shisei historical Chinese 57 sets / 227 views + Gia anime 1,320 + CharaDB anime 440) + Portrait library (1,499 people) = 6,162 reference records / 12,022 local HD images, plus 1,760 reference images hotlinked from the source sites**, with a built-in **AI image studio supporting 11 providers** and a **native ComfyUI custom node plugin (`custom_nodes`)**.

![Gallery overview](docs/preview.jpg)

![AI character studio preview](docs/studio.jpg)

<details><summary>Mobile preview</summary>

![Mobile preview](docs/mobile.jpg)

</details>

**This fork:** English-default edition, maintained by [GeekLord](https://github.com/GeekLord). Forked from the Chinese edition, [anhao/ai-pose-gallery-zh](https://github.com/anhao/ai-pose-gallery-zh), maintained by Anhao ([X @anhao_ai](https://x.com/anhao_ai)). Upstream live demo: <https://ai-pose-gallery.anhao.app/>

**Original sites:**
- Pose library (mannequin): <https://ai-pose-gallery.pages.dev/>
- Pose depth library (Depth): <https://ai-pose-depth-gallery.pages.dev/>
- Costume library: <https://ai-costume-gallery.pages.dev/>
- Portrait library: <https://ai-portrait-gallery.pages.dev/>

**Original gallery author:** Gia (@giaaibusi); anime costume author: Taki AI ([@taki_auto](https://x.com/taki_auto) · [CharaDB](https://charadb-2fi.pages.dev/)).

> **Disclaimer (read first):**
> 1. **Learning and creative use only**: This project and its plugins and workflows are **for personal study, human motion research, lawful artistic creation and technical exchange only**. Any use that violates laws or regulations, generates illegal or obscene content, or infringes the lawful rights of others (such as face-swapping real people without authorization) is strictly prohibited.
> 2. **NSFW content warning**: The galleries include some 18+ adult mannequin poses and lingerie / sexy outfit references. Safe Mode (SFW) is on by default and hides them. **Minors must not unlock or access them.**
> 3. **Source and copyright**: The original pose, realistic costume and portrait references come from the public sites of the original author **Gia (@giaaibusi)**; the 440 anime costume sets come from **Taki AI (@taki_auto)** and [CharaDB](https://charadb-2fi.pages.dev/) (see its [LICENSE](https://github.com/taki-ttt/charadb/blob/main/LICENSE)). Copyright stays with the respective authors. This repository is a translation and engineering archive for study; reselling the gallery images as a bundle is prohibited. Users bear sole legal responsibility for any unlawful use.

---

## What is this

The original sites are three AI art reference galleries (poses, costumes, portraits) published by Gia (@giaaibusi), with all metadata in Japanese, spread across three separate sites. Version 2.0 of this project **merged the three sites into one, fully localized the metadata, and added an AI character composition studio and a native ComfyUI plugin**:

1. **Full local mirror of all three libraries (11,568 images)**: every thumbnail and HD original from the pose library (2,878 mannequin images + 2,878 depth WebP), the costume library (2,814 WebP) and the portrait library (2,998 full-size `1600x2000` HD WebP), for fully offline browsing and static hosting.
2. **Fully localized metadata**: pose systems, pose categories, costume styles, outfit tags, portrait sections, hair lengths and 51 hairstyles, all translated; auto-assembled image prompts carry no Japanese interference.
3. **3-in-1 AI character composition studio (Web Studio)**: a responsive multi-page app built with **React 19 + Tailwind CSS 4 + TypeScript 7 + shadcn/ui + TanStack Router** (PC / tablet / phone):
   - Pick any **portrait + costume + pose (with one-click mannequin / depth switching)** from the three libraries to build a recipe, or randomize a character in one click;
   - Add custom reference images by drag and drop, clipboard paste (`Cmd+V` / `Ctrl+V`) or URL;
   - Built-in **direct connections to 11 AI image providers** (Google Gemini, OpenAI GPT Image, Alibaba Cloud Bailian Qwen, ByteDance Volcano Ark Doubao, PixAI, FAL, Runware AI, Bria AI, Meta Muse Image, a custom OpenAI-compatible API, and **local ComfyUI**), with generation history persisted locally in **IndexedDB**.
4. **Native ComfyUI custom node plugin (`custom_nodes`)**: this repository is also a plug-and-play ComfyUI plugin. Clone it into `ComfyUI/custom_nodes/` to get **4 custom nodes (pose / costume / portrait / 3-in-1 character recipe)** on the ComfyUI canvas (the pose and recipe nodes have a built-in `use_depth` toggle that can feed ControlNet Depth directly) plus a built-in **visual picker popup covering all 6,162 records**.

---

## Core features

### 1. Three reference galleries (poses / costumes / portraits)
- **Pose library (`/poses`)**: 4 systems (full-body solo, standard / full-body solo, sexy / upper-body solo / two-person), 26 action categories, 288 pose groups, 5 views (front / three-quarter / side / back / top-down), **grouped / per-image browsing**, multi-angle switching inside cards, and **one-click [ mannequin | depth (Depth) ] preview and download switching**.
- **Costume library (`/costumes`)**: 8 outfit categories (spring / summer / autumn / winter / lingerie and sleepwear / sexy / swimwear and vacation / party and formal), 86 detail tags and English prompt keywords.
- **Portrait library (`/portraits`)**: 2 sections (face reference 893 / styling and mood 606), 4 hair lengths (short / medium / medium-long / long), 51 hairstyles, with **curated collections** and **top charts** one-click filters.
- **Unified experience**: live keyword search, lightbox HD preview and download, one-click "add to recipe".

### 2. AI character composition studio (`/studio`)
- **3+N reference combination**: 3 core slots (portrait / costume / pose, the pose slot has a live [ mannequin | depth ] switch) plus any number of custom reference images (upload, drag and drop, clipboard paste, or image URL).
- **Reference collage preview and export**: view the 3-in-1 HD reference collage in a popup (`1800x1200` canvas, composed live) and download it as PNG in one click.
- **12 style presets and structured prompts**: No preset (follow the references), realistic portrait photography, Japanese/Korean magazine editorial, vintage film photography, 2.5D game key art, Japanese anime illustration, Makoto Shinkai-style anime film, Japanese black-and-white manga screentone, 3D next-gen character render, 3D designer toy figure, cyberpunk neon, and character design sheet (pure white background). Prompts are assembled automatically from the selected materials.
- **11 AI image providers with advanced parameters**:
  - **Google Gemini**: `gemini-3.1-flash-image-preview`, `gemini-3-pro-image-preview`, `gemini-2.5-flash-image` (aspect ratio `aspectRatio`, resolution 1K/2K/4K)
  - **OpenAI GPT Image**: `gpt-image-2.5`, `gpt-image-2`, `gpt-image-1.5`, `gpt-image-1` (`/v1/images/edits` with JSON URL input or multipart upload, size, quality, background transparency)
  - **Alibaba Cloud Bailian Qwen**: `qwen-image-3.0-pro`, `qwen-image-2.1-pro`, `qwen-image-2.0-pro`, `qwen-image-edit-plus` (multi-image reference input via `multimodal-generation`, smart prompt rewriting `prompt_extend`, watermark toggle)
  - **ByteDance Volcano Ark Doubao**: `doubao-seedream-5-0`, `doubao-seedream-4-5-251128`, `doubao-seedream-4-0-250828`, `doubao-seededit-3-0-i2i-250628` (multi-image fusion `image: [...]`, 2K/4K resolution)
  - **PixAI**: `Tsubaki.3` and `Tsubaki.3 Flash` with resumable background tasks (aspect ratio, resolution, generation mode).
  - **FAL (fal.ai)**: queue API with automatic polling; edit models such as `fal-ai/nano-banana/edit`, Kontext and Qwen Image Edit receive all reference images, text-to-image models such as FLUX use the prompt only.
  - **Runware AI**: synchronous `imageInference` calls; reference images are passed via `inputs.referenceImages` (for example with `minimax:h3@image`), and any model can be used by its AIR id.
  - **Bria AI**: Fibo 2 over the v2 API (`/v2/image/edit` with up to 4 reference images, `/v2/image/generate` without).
  - **Meta Muse Image**: Meta Model API (`api.meta.ai`, OpenAI-compatible `/v1/images/edits` and `/v1/images/generations`) with `muse-image-1.0`.
  - **Custom API (OpenAI-compatible)**: any endpoint that speaks the OpenAI image shapes (`/v1/images/edits` JSON or `/v1/chat/completions`) with your own Base URL, key and model id.
  - **Local ComfyUI workflow engine**: uploads the 3-in-1 collage and individual portrait/costume/pose images to a local ComfyUI (`/upload/image`), injects them into custom API workflow placeholders or auto-detects nodes, submits to the `/prompt` queue and polls for results; supports importing and exporting generic `.api.json` workflow templates.
- **Background generation across pages, with IndexedDB history**: switching pages does not interrupt running generation requests; results are saved to browser IndexedDB (avoiding `localStorage` limits), with prompt reuse and original image download.

> Model list, workflow notes and local setup for the local ComfyUI three-image composition (Qwen Image Edit 2509): [docs/comfyui-local.md](docs/comfyui-local.md).

> Dynamic advanced parameters after API import, design-sheet reference uploads and optional display declarations: [ComfyUI workflow advanced parameters](docs/comfyui-workflow-parameters.md).

> WebSocket live progress, HTTP fallback and refresh recovery: [ComfyUI task connection and recovery](docs/comfyui-task-tracking.md).

### 3. ComfyUI native custom node plugin (`comfyui_plugin/`)
Clone this repository into `ComfyUI/custom_nodes/ai-pose-gallery-zh` and the ComfyUI canvas right-click menu gains 4 nodes under **"AI Character 3-in-1 Reference Gallery"**:
- **AI Pose Reference (`PoseGalleryNode`)**: outputs `pose image (IMAGE)`, `image ID`, `pose prompt` (with a `use_depth` toggle to output the mannequin or the depth map)
- **AI Costume Reference (`CostumeGalleryNode`)**: outputs `costume image (IMAGE)`, `image ID`, `Chinese costume description`, `English costume prompt`
- **AI Portrait Reference (`PortraitGalleryNode`)**: outputs `portrait image (IMAGE)`, `image ID`, `portrait hairstyle description`
- **AI Character 3-in-1 Recipe (`CharacterRecipeNode`)**: one node outputs `portrait image`, `costume image`, `pose image (with use_depth depth switching)`, the `3-in-1 collage`, plus auto-assembled `Chinese composition prompt` and `English composition prompt`, with a built-in **visual picker popup for all 6,162 records (including a depth preview toggle)** and live thumbnail previews inside the node.

### 4. Interface language: English (default in this fork) / Chinese / Thai
- The flag button at the top right switches **English / Chinese / Thai**; the choice is saved in browser `localStorage`. On a first visit the language follows the browser: `th*` gets Thai, `zh*` gets Chinese, and everything else gets English.
- The underlying data is unchanged by the display language: English and Thai are display layers only. UI strings live in `src/i18n/locales/`; data labels (pose names, costume names, categories, tags, hairstyles) live in `data/i18n/<lang>/`, indexed by the original ids. Anything untranslated falls back to Chinese.
- Prompts sent to image models always use the original data, regardless of interface language; Safe Mode (SFW) rules are unchanged.

---

## Data scale

| Library | Categories / systems | Records | Local image files |
| --- | --- | ---: | ---: |
| **Pose library (mannequin)** | Full-body standard (365) · Full-body sexy (399) · Upper body (400) · Two-person (275) | 1,439 | 2,878 (thumbnails `.jpg` + originals `.png`) |
| **Pose depth maps** | One-to-one with the 1,439 pose ids (`POSE-DB-02`) | 1,439 (shared index) | 2,878 (thumbnails `.webp` + originals `.webp`) |
| **Costume library (Gia realistic)** | Spring (215) · Summer (254) · Autumn (244) · Winter (253) · Lingerie and sleepwear (199) · Sexy (140) · Swimwear (54) · Formal (48) | 1,407 | 2,814 (thumbnails `.webp` + originals `.webp`) |
| **Historical Chinese costumes (Shisei)** | Dynasties from Shang to Qing (front / three-quarter / side / back views) | 57 (227 views) | 454 (thumbnails `.webp` + originals `.png`) |
| **Anime costumes (Gia anime)** | Spring · Summer · Autumn · Winter · Lingerie and sleepwear · Sexy · Swimwear · Formal | 1,320 | Hotlinked from the source site; not stored in this repo or its release packages |
| **Anime costumes (CharaDB)** | 15 categories, Chinese names with original Danbooru tags | 440 | Hotlinked from the source site; not stored in this repo or its release packages |
| **Portrait library** | Face reference (893) · Styling and mood (606) / Short hair (727) · Medium (376) · Medium-long (260) · Long (136) | 1,499 | 2,998 (thumbnails `.webp` + `1600x2000` originals `.webp`) |
| **Total** | **All three galleries (with mannequin + depth dual views)** | **6,162** | **12,022** |

---

## Using it in ComfyUI (two modes)

### Mode A: install as a native ComfyUI plugin (pick images inside the ComfyUI canvas)

No extra Python dependencies are needed (it reuses ComfyUI's own `torch`, `numpy`, `Pillow`, `aiohttp`):

```bash
cd /path/to/ComfyUI/custom_nodes
git clone --depth 1 https://github.com/GeekLord/ai-pose-gallery-zh.git
```

After restarting ComfyUI:
1. Right-click on empty canvas space, then **Add Node** and the **AI Character 3-in-1 Reference Gallery** category;
2. Choose the **AI Character 3-in-1 Recipe** node, or a single pose / costume / portrait node;
3. Click the **"Open 3-in-1 picker (6,162 images)"** button on the node (or click the thumbnail on the node) to filter by category, view and hair length, or search, then insert the pick into the node in one click. The node outputs an `IMAGE` tensor plus Chinese and English prompts.

### Mode B: drive a local ComfyUI API from the web studio

If you pick images in the web version (online or local `pnpm dev`) and want generation to run on your own ComfyUI:
1. Start local ComfyUI with CORS enabled:
   ```bash
   python main.py --enable-cors-header "*"
   ```
2. Open the **API Settings** page in this workbench, switch to **Local ComfyUI**, and click "Test connection" (default `http://127.0.0.1:8188`);
3. Import a `.json` file exported from ComfyUI via `Workflow -> Export (API)` (supports the `{{prompt}}`, `{{seed}}`, `{{width}}`, `{{height}}`, `{{composite_image}}`, `{{portrait_image}}`, `{{costume_image}}` and `{{pose_image}}` placeholders, or auto-matching of `CLIPTextEncode` / `KSampler` / `LoadImage` nodes), or export the built-in generic workflow template from the **Studio** in one click.

---

## Tech stack and repository layout

- **Frontend**: React 19.3 + TypeScript 7.0 + Vite 8 (Rolldown)
- **Routing and state**: TanStack Router + TanStack Query + IndexedDB local storage
- **Styling and components**: Tailwind CSS 4.3 + shadcn/ui (Radix UI) + Lucide Icons
- **ComfyUI plugin**: Python (`aiohttp` + `Pillow` + `torch`) + LiteGraph frontend extension
- **Code quality**: Oxlint + Oxfmt

```text
.
├── __init__.py             # ComfyUI custom node plugin entry point (NODE_CLASS_MAPPINGS / WEB_DIRECTORY)
├── comfyui_plugin/         # Native ComfyUI plugin module
│   ├── nodes.py            # The 4 ComfyUI nodes: pose / costume / portrait / 3-in-1 recipe
│   ├── routes.py           # PromptServer local directory and image static routes
│   └── web/                # Node thumbnail previews and the visual picker popup (extension.js / style.css)
├── src/
│   ├── components/         # Shared components, AppLayout responsive navigation, GalleryLightbox, RecipeDock
│   ├── routes/             # Pages: overview (index), poses, costumes, portraits, studio, settings, guide
│   ├── i18n/               # UI languages (English default in this fork, zh / th available; locales/ holds UI strings)
│   ├── services/           # Clients for the AI image providers (aiGenerator.ts) and canvas collage composition (canvasComposer.ts)
│   ├── store/              # Global recipe, generation state and IndexedDB history (studioStore.tsx)
│   ├── lib/                # Data loader (dataLoader.ts) and IndexedDB helpers (idbStorage.ts)
│   └── types/              # Data structures for the three libraries and the AI providers (gallery.ts)
├── functions/api/proxy.ts  # Cloudflare Pages Functions / Workers same-origin CORS proxy (/api/proxy)
├── worker.ts               # Cloudflare Workers entry (static ASSETS + /api/proxy route)
├── wrangler.jsonc          # Cloudflare Workers configuration
├── data/
│   ├── pose.json / pose-zh.json                 # Pose library original data and Chinese data (1,439 records)
│   ├── costume.json / costume-zh.json           # Costume library original data and Chinese data (1,407 records)
│   ├── portrait.json / portrait-zh.json         # Portrait library original data and Chinese data (1,499 records)
│   ├── meta-zh.json / *-meta-zh.json            # Chinese system/category metadata and top charts for the three libraries
│   ├── i18n/en/ · i18n/th/                      # English / Thai data labels (indexed by original id, display only)
│   └── translations.csv                         # Japanese-Chinese translation table
├── thumbs/                 # Thumbnails (poses at root + depth/ + costume/ + portrait/)
├── img/                    # HD originals (poses at root + depth/ + costume/ + portrait/)
├── scripts/
│   ├── download.py         # Four-site concurrent downloader (DATASET=all|pose|depth|costume|portrait)
│   ├── i18n.py             # Japanese-to-Chinese dictionary and portrait hairstyle / costume tag mappings
│   ├── apply_translation.py# Regenerates the three libraries' *-zh.json Chinese data and search indexes
│   ├── verify.py           # Verifies local image completeness (existence / size / file headers)
│   └── build.sh            # Builds the Cloudflare release directory dist/
├── skills/                 # Agent skill packs for pose / costume / portrait search
└── README.md
```

---

## Local development and build

Requires **Node.js 20+** and **pnpm**:

```bash
# 1. Install dependencies
pnpm install

# 2. Start the local dev server (default http://localhost:5173)
pnpm dev

# 3. Type check + production build + lint
pnpm build && pnpm lint
```

### Data and image maintenance scripts (Python 3)

```bash
# Fetch / complete the images from the source sites (existing files are skipped, resumable)
python3 scripts/download.py
WORKERS=64 python3 scripts/download.py   # adjust concurrency

# After editing the dictionary in scripts/i18n.py, regenerate the Chinese JSON for the three libraries
python3 scripts/apply_translation.py

# Verify all image files are complete
python3 scripts/verify.py
```

---

## Deploying to Cloudflare (Workers / Pages)

This project ships with [wrangler.jsonc](wrangler.jsonc) and [worker.ts](worker.ts) and supports both **Cloudflare Workers (static Assets + the `/api/proxy` same-origin proxy)** and **Cloudflare Pages**. The repository is about `1.1 GB` with about `11,600` files, every file under `2 MB`, well within Cloudflare free-tier limits (single file at most 25 MiB, at most 20,000 files).

> **Custom proxy origin allowlist (optional)**: `/api/proxy` allows the five official AI API domains by default, and turns on automatically for Alibaba Cloud Bailian (Qwen) or Volcano Ark (Doubao). To proxy a custom relay through the server side, set a comma-separated origin allowlist in the Cloudflare environment variable or `vars.PROXY_ALLOWED_ORIGINS` in `wrangler.jsonc` (exact domains and wildcard subdomains are supported, e.g. `https://api.example.com,https://*.openai.com`).

### Option 1: Cloudflare Workers, automatic or command-line deploy (recommended; the built-in /api/proxy solves Qwen/Doubao CORS)

```bash
# 1. Build the frontend and the static asset directory dist/
bash scripts/build.sh

# 2. Verify locally or in a preview environment
npx wrangler versions upload

# 3. Deploy to Cloudflare Workers
npx wrangler deploy
```

If you connect GitHub in the Cloudflare Dashboard for automatic Workers builds:
- **Build command**: `bash scripts/build.sh`
- **Deploy command**: `npx wrangler deploy`

### Option 2: Cloudflare Pages deploy

1. Sign in to the Cloudflare Dashboard, then **Workers & Pages** -> **Create** -> **Pages** -> **Connect to Git**
2. Select this repository, production branch `main`
3. Build settings:

   | Field | Value |
   | --- | --- |
   | Framework preset | `None` (or `Vite`) |
   | Build command | `bash scripts/build.sh` |
   | Build output directory | `dist` |

---

## Agent skills

`skills/` contains 9 agent skills in `SKILL.md` format, so AI agents can search the pose, costume and portrait references. The original skills' `references/catalog.csv` files use **relative paths** (`../../img/...`) into this repository's `img/`; the anime skill uses source-site URLs and stores no images:

| Skill | Images | Scope |
| --- | ---: | --- |
| `pose-reference-standard` | 365 | Full-body solo, standard |
| `pose-reference-upper` | 400 | Upper-body solo |
| `pose-reference-sexy` | 399 | Full-body solo, sexy (18+) |
| `pose-reference-couple` | 275 | Two-person (18+) |
| `pose-reference-all` | 1,439 | All poses |
| `costume-reference` | 1,068 | Costumes: seasons, party and formal, swimwear and vacation (search by item / color / English keyword) |
| `costume-reference-anime` | 440 | CharaDB anime costumes, online reference images, separate source terms |
| `costume-reference-sexy` | 339 | Costumes: lingerie and sleepwear, sexy outfits (18+) |
| `portrait-reference` | 1,499 | Portraits: face reference, styling and mood, by hair length / 51 hairstyles |

```bash
git clone --depth 1 https://github.com/GeekLord/ai-pose-gallery-zh.git ~/ai-pose-gallery-zh
mkdir -p ~/.claude/skills
for d in ~/ai-pose-gallery-zh/skills/*-reference*; do ln -s "$d" ~/.claude/skills/; done
```

The original skills read `img/` through relative paths, so **symlink** them instead of copying, and keep the whole repository. `costume-reference-anime` uses source-site URLs, stores no images, and is governed by its own source terms. When combining references, follow each source's terms separately.

---

## Anime costumes (CharaDB)

Includes the public **440 sets** of anime costumes from **Taki AI ([@taki_auto](https://x.com/taki_auto))** and [CharaDB](https://charadb-2fi.pages.dev/): the costume page and the ComfyUI picker both support filtering by the top-level **[ All | Realistic | Anime ]** category, 15 subcategories and item color tags, with search by Chinese name, English Danbooru tag and id.

- **Online original image loading**: under the [original author's LICENSE](https://github.com/taki-ttt/charadb/blob/main/LICENSE) (tags are CC0; images are reference-only, redistribution is prohibited, and use with real people or minors is prohibited), this repository includes only the Chinese translations and tag metadata (`data/costume-anime-zh.json`); images load online from the source site and are not distributed with this repository.
- **Data update script**:
  ```bash
  python3 scripts/import_charadb.py
  ```

## Disclaimer and copyright

1. **Lawful use and learning purposes (no illegal use)**
   - This project (the frontend workbench, ComfyUI plugin, workflow templates and agent skills) is **for personal study, human anatomy research, drawing pose reference and technical exchange only**.
   - **Any unlawful use is strictly prohibited**, including generating, producing or spreading obscene or pornographic material, violent or terrorist content, or false or illegal information, and using real people's photos for face-swapping or deepfake synthesis without their explicit authorization, infringing portrait, privacy or reputation rights.
   - This workbench is a purely frontend / local tool. Every AI generation request runs through a cloud API the user configures, or the user's own local ComfyUI. The platform collects and stores none of the images users upload or generate. **Users bear full legal responsibility for their uploaded materials and generated content; the repository's authors and contributors accept no responsibility for any improper or unlawful use.**
2. **NSFW (18+) content statement**
   - The galleries include some adult 3D mannequin poses (full-body solo, sexy; two-person) and sexy / lingerie outfit references, intended for illustrators and creators practicing human motion and light and shadow.
   - The site and plugin enable **Safe Mode (SFW)** by default, which blocks those categories. **Anyone under 18 must not turn Safe Mode off or access that content.**
3. **Data sources and copyright**
   - Copyright in the original pose (`ai-pose-gallery.pages.dev`), costume (`ai-costume-gallery.pages.dev`) and portrait (`ai-portrait-gallery.pages.dev`, CC0 1.0) images and original data in this repository belongs to the original author **Gia (@giaaibusi)**.
   - This repository is a localization and frontend engineering archive; it claims no rights over the original images. **Extracting images from this repository for commercial resale or paid distribution is strictly prohibited.** If the original author objects to this mirror archive, please contact the maintainer and it will be dealt with immediately.
4. **Open source license**
   - The frontend application code (`src/`), the ComfyUI plugin (`comfyui_plugin/`) and the data processing scripts (`scripts/`) are open source under the [MIT license](LICENSE); that license **does not cover** the images and original data in `img/`, `thumbs/` and `data/`.
