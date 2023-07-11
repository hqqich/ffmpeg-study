
## 指令

#### ffmpeg -formats

查看支持的视频文件格式

#### ffmpeg -help

查看帮助信息

#### ffmpeg -codecs

查看支持的所有编解码器

#### ffmpeg -encoders

查看支持的编码器

#### ffmpeg -decoders

查看支持的解码器

#### ffmpeg -h muxer=flv

查看 flv 格式封装器的参数支持

#### ffmpeg -h demuxer=flv

查看 flv 格式解封装器的参数支持

#### ffmpeg -h encoder=h264

查看H.264(AVC)编码参数支持

#### ffmpeg -h decoder=h264

查看H.264(AVC)解码参数支持

#### ffmpeg -h filter=colorkey

查看colorkey滤镜的参数支持

## 封装，编码

- 通过 libavformat 库进行封装和解封装
- 通过 libavcodec 库进行编码和解码

## 例子

### `ffmpeg -i input.rmvb -vcodec mpeg4 -b:v 200k -r 15 -an output.mp4`

- 转封装格式从RMVB格式转换为MP4格式
- 视频编码从RV40转换为MPEG4格式
- 视频码率从原来的 377kbit/s转换为200kbit/s
- 视频帧率从原来的 23.98fps转换为15fps
- 转码后的文件中不包括音频(-an参数）


## ffprobe 使用

### `ffprobe -show_packets 1G.mp4`

查看多媒体数据包信息

### `ffprobe -show_data -show_packets 1G.mp4`

组合参数查看包具体数据

### `ffprobe -show_format 1G.mp4`

显示视频封装格式

### `ffprobe -show_frames 1G.mp4`

显示视频封装的帧信息

### `ffprobe -show_streams 1G.mp4`

查看多媒体文件中的流信息

- `ffprobe -of xml -show_streams 1G.mp4 > a.xml`  将格式的xml数据覆盖到a.xml中

- `ffprobe -of xml -show_streams 1G.mp4 >> b.xml` 将格式的xml数据追加到b.xml中

- `ffprobe -of ini -show_streams 1G.mp4 > c.ini`  将格式的ini数据覆盖到c.ini中

- `ffprobe -of flat -show_streams 1G.mp4 > d.flat` 将格式的flat数据覆盖到d.flat中

- `ffprobe -of json -show_streams 1G.mp4 > e.json` 将格式的json数据覆盖到e.json中

- `ffprobe -of csv -show_streams 1G.mp4 > f.csv` 将格式的csv数据覆盖到f.csv中


### `ffprobe -show_frames -select_streams v -of xml 1G.mp4`

使用select_streams可以只查看音频(a)、视频 (v)、 字幕（ s）的信息， 例如配合show_ frames查看视频的frames信息

- `ffprobe -show_frames -select_streams v -of xml 1G.mp4 > a.xml`  将格式的xml数据覆盖到a.xml中


## ffplay 命令

> fplay不仅仅是播放器，同时也是测试ffmpeg的codec引擎、format引擎，以及filter引擎的工具， 并且还可以进行可视化的媒体参数分析， 其可以通过ffplay --help进行查看：

### `ffplay --help`

获取帮助文档

### `ffplay -ss 30 -t 10 1G.mp4`

视频的第30 秒开始播放， 播放10 秒钟的文件



## `ffmpeg -i 1G.mp4 1G.avi`

> 转换视频容器

- 获得输入源 1G.mp4
- 转码
- 输出文件 1G.avi

也可以使用以下命令 `ffmpeg -i 1G.mp4 -f avi 1G.dat`

`-f` 指定了输出文件的格式

解封装(Demuxing) => 解码(Decoding) => 编码(Encoding) => 封装📦(Muxing)

![test](./images/2023-07-11 20.58.20.png)
