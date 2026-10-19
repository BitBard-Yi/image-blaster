# IMAGE-BLASTER

IMAGE-BLASTER turns a source image into a local, explorable 3D environment with generated object meshes and sound effects. Use the repository skills in `.agents/skills/` for the repeatable image-to-world workflows and the scripts in `.agents/scripts/` for provider calls and local asset management.

## Project guidance

- Read `.agents/rules/project.md` for the generated-file layout, indexed asset convention, and IMAGE-BLAST ordering.
- At the start of an IMAGE-BLAST request, run `bash .agents/hooks/setup-check.sh` to report missing API keys and staged input.
- Use `image-blast-project` before another Image Blast skill when a project under `worlds/<slug>/` does not already exist.
- Use one focused skill for each generation request. Keep paid provider requests explicit and preserve request metadata so unfinished work can resume.
- Inspect generated directories with `ls -a` before reading JSON state. Generated assets are disk-first; provider URLs in JSON are provenance and resume data only.
- Use `node .agents/scripts/project/show-folder.mjs <path>` when the user asks to open a project folder. Use `node .agents/scripts/project/show-url.mjs <world-slug>` to report the local viewer URL.
- Do not load generated PNG, JPG, WEBP, or audio files into context for routine checks. Use the viewer or folder helper when the user wants to inspect an artifact.

## Setup

1. Copy `.env.example` to `.env`.
2. Set `WORLD_LABS_API_KEY` for world generation and `FAL_KEY` for 3D, SFX, and image editing.
3. Install dependencies with `bun install`.

## Verification

- Run `bun run test` for the Vitest suite.
- Run `bun run typecheck` for TypeScript checks.
- Run `bun run build` for the production viewer build.
- Keep unrelated user changes intact when editing the repository.
