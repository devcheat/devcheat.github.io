# FFmpeg Command Line

## Using CUDA

### Full hardware transcode with NVDEC and NVENC:
```bash
ffmpeg -hwaccel cuda -hwaccel_output_format cuda -i input -c:v h264_nvenc -preset slow output
```

### ffmpeg was compiled with support for libnpp, it can be used to insert a GPU based scaler into the chain:
```cmd
ffmpeg -hwaccel_device 0 -hwaccel cuda -i input -vf scale_npp=-1:720 -c:v h264_nvenc -preset slow output.mkv
```
The `-hwaccel_device` option can be used to specify the GPU to be used by the hwaccel in ffmpeg.

### FHD 1080p 60FPS Dolby Digital 5.1 -Setting
```bat
@echo off

echo "Using CUDA to enhance FHD1080p with 60 FPS and Dolby Digital 5.1"
set input=%1
set output=%2
set def="1080p F60 5.1"

ffmpeg -hwaccel_device 0 -hwaccel cuda -i "%input%" -vf scale=-1:1080 -r 60 -c:v hevc_nvenc -preset slow -ac 6 -map 0 -c:a ac3 "FHD_60FPS_DolbyDigital_%output%"
```

## Audio

### Individual channels:
NAME |DESCRIPTION
--|--
FL |front left
FR |front right
FC |front center
LFE |low frequency
BL |back left
BR |back right
FLC |front left-of-center
FRC |front right-of-center
BC |back center
SL |side left
SR |side right
TC |top center
TFL |top front left
TFC |top front center
TFR |top front right
TBL |top back left
TBC |top back center
TBR |top back right
DL |downmix left
DR |downmix right
WL |wide left
WR |wide right
SDL |surround direct left
SDR |surround direct right
LFE2 |low frequency 2

### Standard channel layouts:
NAME |DECOMPOSITION
--|--
mono |FC
stereo |FL+FR
2.1 |FL+FR+LFE
3.0 |FL+FR+FC
3.0(back) |FL+FR+BC
4.0 |FL+FR+FC+BC
quad |FL+FR+BL+BR
quad(side) |FL+FR+SL+SR
3.1 |FL+FR+FC+LFE
5.0 |FL+FR+FC+BL+BR
5.0(side) |FL+FR+FC+SL+SR
4.1 |FL+FR+FC+LFE+BC
5.1 |FL+FR+FC+LFE+BL+BR
5.1(side) |FL+FR+FC+LFE+SL+SR
6.0 |FL+FR+FC+BC+SL+SR
6.0(front) |FL+FR+FLC+FRC+SL+SR
hexagonal |FL+FR+FC+BL+BR+BC
6.1 |FL+FR+FC+LFE+BC+SL+SR
6.1(back) |FL+FR+FC+LFE+BL+BR+BC
6.1(front) |FL+FR+LFE+FLC+FRC+SL+SR
7.0 |FL+FR+FC+BL+BR+SL+SR
7.0(front) |FL+FR+FC+FLC+FRC+SL+SR
7.1 |FL+FR+FC+LFE+BL+BR+SL+SR
7.1(wide) |FL+FR+FC+LFE+BL+BR+FLC+FRC
7.1(wide-side) |FL+FR+FC+LFE+FLC+FRC+SL+SR
octagonal |FL+FR+FC+BL+BR+BC+SL+SR
hexadecagonal |FL+FR+FC+BL+BR+BC+SL+SR+TFL+TFC+TFR+TBL+TBC+TBR+WL +WR
downmix |DL+DR

### upmix to 5.1
```bash
ffmpeg -i input.mkv -filter_complex "[0:a]pan=5.1(side)|FL=FL|FR=FR|LFE<FL+FR|SL=FL|SR=FR[a]" -map 0 -map -0:a -map "[a]" -c copy -c:a flac output.mkv

ffmpeg -i "${INPUT}" -filter_complex "[0:a]pan=5.1(side)|FL = FL|FR = FR|FC < 0.5*FL + 0.5*FR|LFE < FL+FR|SL = FL|SR = FR[a]" -map 0 -map -0:a -map "[a]" -c copy -c:a ac3 "${OUTPUT}"

ffmpeg -i input.mkv -filter_complex "[0:a]pan=5.1(side)|FL=FL|FR=FR|LFE<FL+FR|SL=FL|SR=FR[a]" -map 0 -map -0:a -map "[a]" -c copy -c:a eac3 output.mkv

```

### upmix to 6.1
```bash
ffmpeg -i input.mkv -filter_complex "[0:a]pan=6.1(side)|FL=FL|FR=FR|LFE<FL+FR|SL=FL|SR=FR|FC<FL*0.5+FR*0.5" -map 0 -map -0:a -map "[a]" -c copy -c:a flac output.mkv
```
