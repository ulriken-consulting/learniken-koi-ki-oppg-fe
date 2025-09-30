# Workshop Task: Personal Library & Book Reviews App

## 1. Overview

Build a small full‑stack web app where users can search for books via the free OpenLibrary API, add them to their personal library ("Reading", "Completed", "Wishlist"), and write short reviews & ratings. Focus on clean separation of concerns and using AI assistance (GitHub Copilot) for boilerplate, refactors, and small enhancements.

## 2. Core MVP Features

-   Search books by title / author (OpenLibrary) and display results (title, authors, cover, first publish year).
-   Add a book from search results into the local collection with a chosen shelf/status.
-   View personal library filtered by status (Reading, Completed, Wishlist, Abandoned optional).
-   Add / edit / delete a review (rating 1–5 + free text) for books in library.
-   Persist data locally (SQLite or JSON file) so it survives restarts.
-   Basic responsive UI (list + detail panel or modal).

## 3. OpenLibrary Integration (No API key needed)

Example endpoints:

-   Search: `https://openlibrary.org/search.json?q=clean%20code&limit=10`
-   Covers: `https://covers.openlibrary.org/b/id/{coverId}-M.jpg`
-   Work details (optional enrich): `https://openlibrary.org/works/{workId}.json`

Normalize returned data to a minimal shape you store locally, or just store the openlibrary key, and retrieve data externally every time.

## 4. Front-End Views

1. Search Page / Panel: search box + results list + "Add" buttons (choose status in a small select).
2. Library Page: tabs or filter for statuses; each card shows title, authors, status, rating snippet.
3. Book Detail / Drawer: enriched data + review form (create/update) + status changer.

## 5. Suggested Stack

-   Server: Node.js + Express (TypeScript) OR FastAPI (Python) if preferred.
-   Persistence: SQLite (better-sqlite3 / Prisma) OR fallback JSON file for simplest path.
-   Front-end: Vite + React (TS).
-   Optional testing: ViTest.

## 6. Milestones (Timeboxed Path)

1. (10–15m) Scaffold server + /health + placeholder /api/search returning mock data.
2. (15–25m) Implement real OpenLibrary search service with normalization + caching (in-memory Map by query, TTL 5m).
3. (25–40m) Data layer & migrations (or JSON file) + POST /api/books + GET /api/library.
4. (40–55m) Reviews routes + validation.
5. (55–70m) Front-end search & add to library.
6. (70–85m) Library listing + detail + review form.
7. (Stretch) Enrichment fetch (work details) when opening detail pane.
