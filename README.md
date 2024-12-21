# HM - Modified Version

This project is a modified version of the open-source HM software.

## Modifications
- Add CU size decision algorithm based on [Effective CU Size Decision for HEVC Intracoding](https://ieeexplore.ieee.org/document/6862903)
- Implement HexagonSearch, SquareSearch and FullSearch
- Implement Enhanced DiamondSearch to improve coding quality

# HM Setup and Usage Instructions

## 1. Clone the Repository
```bash
git clone https://vcgit.hhi.fraunhofer.de/jvet/HM.git
```

## 2. Install HM
Follow the [repository](https://vcgit.hhi.fraunhofer.de/jvet/HM.git) instructions to install HM.

## 3. Install FFmpeg
Install FFmpeg on your system.

## 4. Verify FFmpeg Installation
```bash
ffmpeg -version
```

## 5. Convert Video to `.yuv` Format
```bash
ffmpeg -i input.mp4 -pix_fmt yuv420p -s 1920x1080 -r 30 output.yuv
```

## 6. Check Frame Rate and Length
```bash
ffprobe -video_size 1920x1080 -pixel_format yuv420p -f rawvideo -i ~/Downloads/output.yuv
```

## 7. Encode with HM
```bash
./bin/TAppEncoderStatic -c cfg/encoder_randomaccess_main.cfg -i ~/Downloads/output.yuv -b compressed.h265 -wdt 1920 -hgt 1080 -fr 25 -f 9875
```

## 8. Play the Encoded File
```bash
ffplay compressed.h265
```

Change Motion Search Flag
-------------------------------
Change the flag in cfg file to use different MS algorithm.
```bash
FastSearch                    : 4         
# enum MESearchMethod
# {
#   MESEARCH_FULL              = 0,
#   MESEARCH_DIAMOND           = 1,
#   MESEARCH_SELECTIVE         = 2,
#   MESEARCH_DIAMOND_ENHANCED  = 3,
#   MESEARCH_HEXAGON           = 4,
#   MESEARCH_HEXAGON_ENHANCED  = 5,
#   MESEARCH_HEXAGON_CROSS     = 6,
#   MESEARCH_DIAMOND_CROSS     = 7,
# };
```
If you encounter some warnings  in TAppEncCfg when compiling code, please ignore it.

Videos
-------------------------------
V1.mp4 : F1.mp4,
V2.mp4 : 10月.mp4

## AUTHOR
This modified version was developed by:
- Andrea Hsu
- Alec Chan
- Engine Yao

## License
This project is based on [HM](https://vcgit.hhi.fraunhofer.de/jvet/HM.git). Please refer to the original project's license for more details.