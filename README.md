# StageDetect

This program detects water stages using image sequences. Included is the estimation of exterior camera orientation, template 
matching for GCP detection, master retrieval from image sequence, image co-registration, water line 
detection, and transforming 2D points into 3D coordinates.


# Notes
## MacOS Big Sur fix
A patch is required for MacOS Big Sur for the shapely library
You will get the following error:
```
    File "<stdin>", line 1, in <module> 
    File "/Users/pradal/miniconda3/envs/shapeely/lib/python3.8/site-packages/shapely/geos.py", line 113, in <module> 
        free = load_dll('c').free 
    File "/Users/pradal/miniconda3/envs/shapeely/lib/python3.8/site-packages/shapely/geos.py", line 54, in load_dll 
        raise OSError( 
OSError: Could not find lib c or load any of its variants [].
``` 

The fix is documented [On Github](https://github.com/Toblerity/Shapely/issues/888).
In short, you need to patch the file `geos.py` in the installed `shapely` library.  
Change line 138  
from: `free = load_dll('c').free`  
to: `free = CDLL(None).free`
