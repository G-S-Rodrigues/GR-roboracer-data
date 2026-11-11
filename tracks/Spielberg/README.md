# Spielberg

Ground truth: the gym importer's output (`sim.track_importer`) for the track in GR-roboracer `config/tracks/spielberg.yaml`: `Spielberg.png`/`.yaml` are the walls, `Spielberg_centerline.csv` and `Spielberg_raceline.csv` its lines. `NOTICE.md` has the upstream provenance and the regeneration root (`--maps-root` is the `tracks/` folder).

Layout: `maps/<method>/` holds the maps this stack built of the track (each folder has its own README and a PNG); `racelines/<optimizer>/<limit set>/` holds the racelines (`raceline.csv`, `raceline.yaml`, `limits.md`). See the repository README for the grammar of a limit-set name.

Path history: before GR-roboracer's D2 change the ground truth and `NOTICE.md` were in `tracks/Spielberg/maps/Spielberg/`, the survey grid in `.../slam/`, the MOLA map in `.../mola/`, and racelines in `racelines/<vehicle-version>/<optimizer>.csv`. ADR 0009 has the earlier history.
