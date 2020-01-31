
# VR Box

#### QR Code

QR code for the VR BOX from China (the one that cost $25) on Imgur (http://imgur.com/r/GoogleCardboard/HzCCw1M) 
raw image: http://i.imgur.com/HzCCw1M.png
"VR Box from Some Customer" cardboard settings

decoded via zxing.org: https://zxing.org/w/decode?u=http%3A%2F%2Fi.imgur.com%2FHzCCw1M.png

```
    Raw text                goo.gl/elwxBW
    Raw bytes   
    40 d6 76 f6 f2 e6 76 c2   f6 56 c7 77 84 25 70 bb
    69 da 29 6e c8 81 b5 78   3a 6e 63 04 23 06 85 14
    e4 10 ba 06 cc cc cc cc   ce 45 6e 57 00 19 99 99
    99 98 09 ee 2c e0 66 c6   66 4e 60 14 d2 6e 08 1a
    9d 19 58 b8 0a 40 dd 60   74 6a 62 e5 60 4d 2d 58
    88 19 c9 ab 8d 98 16 58   1b 20 66 60 60 66 60 4d
    46 ad 51 cc cd 99 cc cd   85 1e 8f be 
    Barcode format          QR_CODE
    Parsed Result Type      URI
    Parsed Result           http://goo.gl/elwxBW
```
If you browse to it, it just goes to Google Cardboard app: https://vr.google.com/cardboard/download/?p=Cg1Tb21lIEN1c3RvbWVyEgZWUiBCb3gdrkdhPSWPwnU9KhAAAEhCAABIQgAASEIAAEhCWAE1KVwPPToIzcxMvc3MTD1QAGAA

#### Decode VR Profile

Tried to decode image, short url with http://vrembed.org/tools/google_profile_decode.html, no dice, but long URL (https://vr.google.com/cardboard/download/?p=Cg1Tb21lIEN1c3RvbWVyEgZWUiBCb3gdrkdhPSWPwnU9KhAAAEhCAABIQgAASEIAAEhCWAE1KVwPPToIzcxMvc3MTD1QAGAA) gives:

JSON output

```json
    {"vendor":"Some Customer","model":"VR Box","screen_to_lens_distance":0.054999999701976776,"inter_lens_distance":0.05999999865889549,"left_eye_field_of_view_angles":[50,50,50,50],"vertical_alignment":1,"tray_to_lens_distance":0.03500000014901161,"distortion_coefficients":[-0.05000000074505806,0.05000000074505806],"has_magnet":false,"primary_button":0},
```
(looks like distances are in metres, not mm)

vrEmbed Device output
```
    SOMECUSTOMERVRBOX : {name: "Some Customer VR Box",renderMode: VRRenderModes.STEREOANAGLYPH,icon: VRIcons.logoAnaglyph,hfov:50,ipd:59,ipdAdjust: 0,k: [-0.05,0.05] },
```

notice: `"has_magnet":false`

## Viewer Profile Generator

Viewer Profile Generator: https://vr.google.com/cardboard/viewerprofilegenerator/

### parameters

```
    Vendor
    Model
    Primary button type (None: 0, Magnet: 1, Touch: 2, Indirect Touch: 3)
    Screen to lens distance (mm) 
    Inter-lens distance (mm)
    Screen vertical alignment (Bottom: 0, Center: 1, Top: 2)
    Tray to lens-center distance (mm)
    Distortion coefficients:
    k1 
    k2 
    Field-of-view angles:
    Outer (°) 
    Inner (°) 
    Top (°) 
    Bottom (°) 
    Viewer contains some embedded magnets (smartphone’s magnetometer should not be used)
```
```json
    {"vendor":"Some Customer","model":"VR Box","screen_to_lens_distance":0.054999999701976776,"inter_lens_distance":0.05999999865889549,"left_eye_field_of_view_angles":[50,50,50,50],"vertical_alignment":1,"tray_to_lens_distance":0.03500000014901161,"distortion_coefficients":[-0.05000000074505806,0.05000000074505806],"has_magnet":false,"primary_button":0},
```

```json
    {"vendor":"Some Customer",                                              // my name
    "model":"VR Box",                                                       // VR Box with magnet
    "screen_to_lens_distance":0.054999999701976776,                         // 55mm
    "inter_lens_distance":0.05999999865889549,                              // 60mm
    "left_eye_field_of_view_angles":[50,50,50,50],                          // 50, 50, 50, 50
    "vertical_alignment":1,                                                 // Bottom: 0, Center: 1, Top: 2
    "tray_to_lens_distance":0.03500000014901161,                            // 35mm
    "distortion_coefficients":[-0.05000000074505806,0.05000000074505806],   // -0.050, 0.050
    "has_magnet":false,                                                     // make true
    "primary_button":0},                                                    // make 1 (None: 0, Magnet: 1, Touch: 2, Indirect Touch: 3)
```

SUCCESS!
Here is the QR viewer profile generated for: BirdVision VR Box with magnet
`~/Projects/vr/`

(2020-01-31 10:55:30 aargh - where? what machine?)
`/Users/kvogel/Downloads/import/from kvogel-elitebook/Projects/vr`

but doesn't seem to respond to magnet...

software solution?
would need (rooted?) app to receive e.g. websocket signal and simulate click
