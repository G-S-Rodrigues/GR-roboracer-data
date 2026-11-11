# Porto

Ground truth: the official AutoDRIVE-RoboRacer-Racetracks Porto map (`Porto.pgm`, `Porto.yaml`), committed unedited. `NOTICE.md` has the provenance.

Layout: `maps/<method>/` holds the maps this stack built of the track (each folder has its own README and a PNG); `racelines/<optimizer>/<limit set>/` holds the racelines (`raceline.csv`, `raceline.yaml`, `limits.md`). See the repository README for the grammar of a limit-set name.

Path history: before GR-roboracer's D2 change the ground truth and `NOTICE.md` were in `tracks/Porto/maps/Porto/`, the survey grid in `.../slam/`, the MOLA map in `.../mola/`, and racelines in `racelines/<vehicle-version>/<optimizer>.csv`. ADR 0009 has the earlier history.

`config/tracks/porto.yaml` lines 1-2 in GR-roboracer and `NOTICE.md` still name `tracks/Porto/maps/Porto/`: they are the recorded command as run, and the file's sha256 is pinned by the Porto raceline record, so they are history and stay unedited.
