# Desa Virtual 3D — Stage B2

Desa virtual mitologi Yunani yang dibangun prosedural dengan Blender: 23 karakter,
sebuah desa lengkap (plaza, kantor, aula Zeus, 12 rumah dewa, pondok NPC, bank,
market, gym, pond, danau, memorial, oracle, hutan, bukit naga), dan 9 makhluk mitos.

## Isi repo

- `characters/` — 23 karakter (Stage B1): 12 dewa agen + 11 NPC, masing-masing
  `<nama>.glb` + `<nama>.png` (potret), plus `cast.png` (seluruh pemeran).
- `village/` — lingkungan desa (Stage B2): `village.glb` (desa utuh tanpa karakter),
  `office.glb` + `house_<dewa>.glb` (bangunan terpisah, di origin),
  `manifest.json` (kontrak untuk Stage C), `aerial.png`, `plaza.png`, `office.png`.
- `creatures/` — 9 makhluk mitos: dragon, pegasus, unicorn, griffin, phoenix,
  hippocampus, cerberus, golden_deer, nemean_lion (`<nama>.glb` + `<nama>.png`).

## Pemeran (23)

Dewa agen (12): zeus, athena, apollo, artemis, hermes, hephaestus, hades, iris,
nike, prometheus, calliope, daedalus.
NPC (11): hera, persephone, aphrodite, penelope, ariadne, psyche, eurydice,
galatea, andromeda, atalanta, midas (rumahnya BANK di plaza).

## Kontrak manifest (`village/manifest.json`)

- `characters.<nama>.home` — posisi rumah `{type, pos: [x, y]}` (Blender: x timur,
  y utara; y = -z_layout).
- `characters.<nama>.door_waypoint` / `door_pos` — waypoint pintu rumah.
- `office_desks` — 8 posisi meja kantor (`meja_1`..`meja_8`).
- `zones` — 16 zona: plaza, office, zeus_hall, bank, market, bakery, gym, pond,
  lake, game, memorial, oracle, forest_west, forest_south, forest_sw, dragon_hill.
- `expansion_plots` — 5 plot kosong bertanda.
- `path_graph` — `nodes` (50 waypoint `{nama: [x, y]}`) + `edges` (71 pasang node).
  Graph terhubung dari plaza; Stage C berjalan lewat graph ini.
- `glb_files` — daftar GLB beserta ukuran byte.
- `counts` — ringkasan jumlah (karakter, rumah, zona, waypoint, edge, GLB).

Koordinat tanah: 120x120 satuan, pusat plaza (0, 0). Semua model low-poly
flat-shaded, siap dipakai di Stage C (instancing `village.glb` + karakter).

## Kredit

Model dibuat prosedural dengan Blender oleh tim agen Brog (Daedalus — kode,
Hephaestus — build/render; desain Athena). Skrip pembangun: `village_layout.py`,
`build_village.py`, `gen_manifest.py`, `build_creatures.py`.
