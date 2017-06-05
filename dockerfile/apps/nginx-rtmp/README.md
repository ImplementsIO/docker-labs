Alpine nginx with rtmp-module & ffmpeg tools && MPEG-DASH

## Information

- nginx=1.8.1
- nginx-rtmp-module=1.1.7.10

## Usage

### Run

```
docker run --name nrt -p 80:80 -p 443:443 -p 8080:8080 -p 1935:1935
```

### PUSH

```
# HLS
ffmpeg -re -i nju.mp4 -vcodec libx264 -acodec copy -b:v 1M \
	       -s 960x480 -f flv rtmp://localhost/hls/test

# DASH
ffmpeg -re -i nju.mp4 -vcodec libx264 -acodec copy -b:v 1M \
	       -s 960x480 -f flv rtmp://localhost/dash/test
```

### PLAY

```
ffmplay http://localhost/hls/test.m3u8
```

## More

- [dash.js](https://github.com/Dash-Industry-Forum/dash.js)
- [nginx-rtmp](https://github.com/sergey-dryabzhinsky/nginx-rtmp-module)
- [alpine-nginx-rtmp](https://hub.docker.com/r/thonatos/alpine-nginx-rtmp/)