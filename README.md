# Geopath repository
* original repository of ...
* this must exist somewhere else in the interweb, but I dunno where, so here we continue its journey
* used in the AcrossAustria project of the [TU Space Team](https://spaceteam.at/)

## General info

Python Packages installieren:
```cmd
pip install networkx numpy pillow scipy shapely
```

Karte mit Höhendaten erstellen:

```cmd
python gen_grid.py -r 1000 test.npy
```
Auflösung = 10m, Ausgabedatei = "test.npy" 

Verwendet Daten in "ogd-10m-at"

## infos/changelog to get gen_grid.py running again
* OSgeo4w installer: proj installieren, lib fehlt: webp -> 3 extra installs mit dem Namen suchen + anklicken
* SSL stuff: pip install python-certifi-win32
* SSL stuff: verify=False hinzugefügt (not save)
* KeyError: 'M' ..? - use case insensitivity
* MultiPolygon? : added as id 4, will cause problems later
* vector_tile_pb2 - pip install mapbox; pip install mapbox-vector-tile xx - https://github.com/mapbox/vector-tile-py


## Pfad erstellen
```cmd
python find_path.py grid_100x100_nopop.npy 1324653.700182,5978980.789495 1818284.028848,6115076.918357
```
fast resturn
```cmd
python find_path.py grid_100x100_nopop.npy 1324653,5978980 1342387,5982687
```

mit Koordinaten von "https://epsg.io/map#srs=3857"

Start: 1324653.700182,5978980.789495

Ziel: 1818284.028848,6115076.918357
 
Slope Factor indirekt proportional zu tolerierter Steigung

Epsilon (RDP Algorithmus) direkt proportional zu Kompression/Vereinfachung von Pfad

Gütefunktion in geogrid.py Row 228 mit Penalty = "new_g"

https://proj.org/apps/cs2cs.html

Filter for transformations between two coordinate reference systems.

sys.setrecursionlimit(1500) in find_path.py (RDP Algorithmus)

Pfad von cs2cs (C:\OSGeo4W\bin\cs2cs.exe) eingeben in: geotiff.py