# Session summary: 2026-10-29

## Decisions made
1. **Phase 1 project changed from burned area to Almaty air quality (PM2.5).**
   - Reason: possible conflict of interest. At the institute I work on burned-area /
     fire-spread prediction, so personal projects avoid fire topics, institute data,
     code and methods.
   - Considered and rejected: monthly fire-risk forecasting (too close to work),
     Sentinel-2 burn-scar mapping (same domain), hh.kz job-market NLP (backup idea).
2. **Project framing (in README):**
   - Forecast hourly PM2.5 per station for 24 h and 48 h ahead.
   - Data: OpenAQ (sensors) + Open-Meteo (weather history and forecast).
     For future hours, use *forecast* weather, not actual weather, to avoid leakage.
   - Baselines: persistence (value 24 h earlier) and a seasonal profile
     (station × hour × month).
   - Metrics: MAE per horizon, plus recall/precision on hazardous hours.
     Recall matters more.
   - Slices: heating vs. non-heating season, hour, station, weekday.
   - Evaluation: time-based backtesting only, never random splits.
   - Stack: Prefect, Postgres, DVC, MLflow, LightGBM, FastAPI, Docker,
     GitHub Actions, Evidently.
3. **Learning mode added to `ete_ml/CLAUDE.md`:**
   - I write the core code myself.
   - Claude explains, gives hints first, and reviews.
   - Claude gives full solutions only on explicit request.
4. **CLAUDE.md split (agreed, not done yet):**
   - `ete_ml/CLAUDE.md`: personal roadmap. Goes into a private repo `career-roadmap`.
   - `almaty-air-quality/CLAUDE.md`: project-only info. Committed to the project repo.
   - `ete_ml/.gitignore` contains `almaty-air-quality/`. Each repo has its own `.gitignore`.

## Current state
- GitHub: `Bekabaev/almaty-air-quality` (private), branch `main`, up to date.
  - Commits: initial → README rewrite → package rename `burned_area` → `air_quality`.
- Structure: `README.md`, `.gitignore`, `src/air_quality/__init__.py`, `tests/`, `docs/`.
- `almaty-air-quality/CLAUDE.md` exists on the PC but is **empty and untracked**.
- `ete_ml/` is **not a git repo yet**, so `CLAUDE.md` and this summary exist only on the PC.

## Git lessons from today
- `add` → staging, `commit` → local history, `push` → GitHub. Push sends only commits.
- Run `git status` before `push`. "Changes to be committed" means you forgot to commit.
- Rename tracked folders with `git mv old new`.
- With two computers: start a session with `git pull`, end it with `commit` + `push`.

## Next steps (on the laptop)
1. Get `ete_ml/` onto the laptop:
   - On the PC, create the `career-roadmap` repo:
     ```
     cd ete_ml
     git init -b main
     echo almaty-air-quality/ > .gitignore
     git add . && git commit -m "Add roadmap"
     ```
   - Create a private GitHub repo `career-roadmap`, then `git remote add origin ...` and `git push -u origin main`.
   - On the laptop, clone `career-roadmap` as the `ete_ml` folder, and clone
     `almaty-air-quality` inside it (or move the existing clone there).
2. Write `almaty-air-quality/CLAUDE.md` (20–30 lines: project, stack, structure,
   commands, conventions, current step, learning-mode rule), commit it, push it,
   and ask Claude for a review.
3. Explore OpenAQ for Almaty: number of stations, reference vs. low-cost sensors,
   history length, gaps. This is the main project risk.
4. Decide on the hazardous PM2.5 threshold (WHO or AQI) and confirm the 24 h / 48 h horizons.

## Open questions for me to answer
- When the heating season starts, is the change data drift or concept drift (or both)? Why?
- Why is the persistence baseline hard to beat in winter smog?
