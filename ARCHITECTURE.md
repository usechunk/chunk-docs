# Chunk Architecture

## ✅ What ChunkHub Is

ChunkHub is best understood as a **platform + protocol**, not a library.

Specifically:

**ChunkHub =**

- A registry (like Docker Hub, npm registry, PyPI index, Homebrew taps)
- An API service for publishing + discovering modpacks/mod definitions
- The backend that the CLI and GUI interact with
- A standard for describing mods and modpacks (Chunkfiles / formulas)
- A distribution layer that connects Modrinth, CurseForge, GitHub, and local mods

**ChunkHub's job is to be:**

The home for metadata, manifests, formulas, and orchestration — not the mods themselves.

## ❌ What ChunkHub Is Not

ChunkHub is **not**:

- Not a "mod library" like Modrinth or CurseForge
- Not a "code library" imported into apps
- Not a "mod hosting service" (unless you choose to add that)
- Not a simple package repo

Libraries are meant to be embedded in other codebases.

**ChunkHub is meant to be called by tools** (CLI, API consumers), not embedded.

## 🧩 So What About Chunk CLI and Chunk App?

Those are client-facing tools:

### chunk-cli

- An installer
- A downloader
- A formula interpreter
- A pack builder
- A dev tool

### chunk-app

- The GUI wrapper for chunk-cli
- A user-friendly way to browse/search/install
- A pack management app

They talk to ChunkHub — but they are not libraries either.

## 🧠 The Core Model

Here's a clean way to think about it:

**Chunk** = the tooling
- CLI + App + APIs + formulas

**ChunkHub** = the ecosystem
- Registry + Metadata store + Unified mod index

**Modrinth/CurseForge/GitHub** = the sources
- Where the actual mods live

**ChunkHub sits above all of them.**

## 🏗️ System Diagram

```
┌─────────────────────────────────────────────────┐
│                   Users                          │
└─────────────────┬───────────────────────────────┘
                  │
         ┌────────┴────────┐
         │                 │
    ┌────▼─────┐    ┌──────▼──────┐
    │ Chunk CLI │    │  Chunk App  │
    └────┬─────┘    └──────┬──────┘
         │                 │
         └────────┬────────┘
                  │
         ┌────────▼────────┐
         │    ChunkHub     │
         │   (Registry)    │
         └────────┬────────┘
                  │
      ┌───────────┼───────────┐
      │           │           │
 ┌────▼────┐ ┌───▼───┐ ┌────▼────┐
 │Modrinth │ │CurseF.│ │ GitHub  │
 └─────────┘ └───────┘ └─────────┘
```

## 🎯 Key Principles

1. **Separation of Concerns**
   - ChunkHub = metadata & orchestration
   - Sources = actual mod files
   - Tools = user interaction

2. **Unified Interface**
   - One API for all mod sources
   - Consistent tooling across platforms
   - Standard formula format

3. **Decentralized Storage**
   - Mods stay at their sources
   - ChunkHub only stores references
   - No unnecessary duplication

4. **Developer-First**
   - CLI for automation
   - API for integration
   - Formulas for reproducibility
