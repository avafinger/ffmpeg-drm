## ffmpeg-drm

Modified ffmpeg-drm to run on Rockchip platform.
Tested on ROCK 5B and NanoPi R6S.

## Build and run

**Statically linked example:**

    gcc -g0 -O2 -o ffmpeg-drmx ffmpeg-drm.c -I../ffmpeg-rk/ -I/usr/include/libdrm ../ffmpeg-rk/libavcodec/libavcodec.a ../ffmpeg-rk/libavformat/libavformat.a ../ffmpeg-rk/libavutil/libavutil.a ../ffmpeg-rk/libswresample/libswresample.a ../ffmpeg-rk/libavcodec/libavcodec.a -lz -lm -lpthread -ldrm -lrockchip_mpp -lvorbis -lvorbisenc -ltiff -lopus -logg -lmp3lame -llzma -lrtmp -lssl -lcrypto -lbz2 -lxml2

**Running some movies:**

  * Drop to CLI
  
    sudo systemctl stop lightdm
  
  * Running

    **sudo ./ffmpeg-drm --video ./Sintel_1080_10s_5MB.mp4**

        [av1_rkmpp @ 0x559c1c73f0] Decoder noticed an info change (1920x818), stride(1920x824), format=0
        1677185462:00496624 :Pixel format avframe: NV12 (0x3231564e)
        1677185462:00626123 :  ffmpeg-drm: connector: connected
        1677185462:00626345 :  ffmpeg-drm: available connector(s)
        1677185462:00626456 :  ffmpeg-drm: connector id:421
        1677185462:00626480 :  ffmpeg-drm: 	encoder id:420 crtc id:68
        1677185462:00626506 :  ffmpeg-drm: 	width:1920 height:1080
        1677185462:00627182 :  ffmpeg-drm: 	Found NV12 plane_id: 54


    **sudo ./ffmpeg-drm --video ./sample_3840x2160.hevc**

        [hevc @ 0x5574bf5150] Stream #0: not enough frames to estimate rate; consider increasing probesize
        [hevc_rkmpp @ 0x5574d20790] Decoder noticed an info change (3840x2160), stride(3840x2160), format=0
        1677185479:00636123 :Pixel format avframe: NV12 (0x3231564e)
        1677185479:00769539 :  ffmpeg-drm: connector: connected
        1677185479:00769790 :  ffmpeg-drm: available connector(s)
        1677185479:00769869 :  ffmpeg-drm: connector id:421
        1677185479:00769893 :  ffmpeg-drm: 	encoder id:420 crtc id:68
        1677185479:00769918 :  ffmpeg-drm: 	width:1920 height:1080
        1677185479:00770594 :  ffmpeg-drm: 	Found NV12 plane_id: 54


    **sudo ./ffmpeg-drm --video ./jellyfish-20-mbps-hd-hevc-10bit.mkv**

        [hevc_rkmpp @ 0x55a4eecbf0] Decoder noticed an info change (1920x1080), stride(2816x1080), format=1
        1677185512:00176124 :Pixel format avframe: NV15 (0x3531564e)
        1677185512:00306438 :  ffmpeg-drm: connector: connected
        1677185512:00306681 :  ffmpeg-drm: available connector(s)
        1677185512:00306848 :  ffmpeg-drm: connector id:421
        1677185512:00306978 :  ffmpeg-drm: 	encoder id:420 crtc id:68
        1677185512:00307194 :  ffmpeg-drm: 	width:1920 height:1080
        1677185512:00308233 :  ffmpeg-drm: 	Found NV15 plane_id: 54


## Dependencies

* FFmpeg with Rockchip HW decode (rkmpp)
* FFmpeg with DRM_PRIME (no rga conversion)

## References 

* https://github.com/BayLibre/ffmpeg-drm/
* https://github.com/JeffyCN/FFmpeg
