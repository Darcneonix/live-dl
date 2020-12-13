# Live Downloader

Download live streams from YouTube.

## Features

- URL guessing: this script will try it best to guess what you pass to it, the following URLs/URIs should all work:
  - https://www.youtube.com/channel/UC1opHUrw8rvnsadT-iGp7Cg/live
  - https://www.youtube.com/channel/UC1opHUrw8rvnsadT-iGp7Cg
  - https://www.youtube.com/watch?v=S3CAGeeMRvo
  - https://www.youtube.com/playlist?list=UU1opHUrw8rvnsadT-iGp7Cg
  - S3CAGeeMRvo
  - UC1opHUrw8rvnsadT-iGp7Cg
- Monitor your favorite YouTube channel and download streams when live starts
- Email/Slack notifications when stream starts or finish downloading
- Writing streamer metadata (author/channel name, description, year) via FFmpeg
- Embed YouTube thumbnail as video cover via ~~AtomicParsley~~ (now handled by FFmpeg)
- Download subtitles if available
- Keywords filter: only download streams that match specific keywords in title
- Convert TS to ~~MP4~~ MKV after downloading

## Storage
The downloaded file is saved to the folder mentioned in config.yml.

I've changed the name to save as youtube video id, the folder name as the channel's first word.

## Dependencies

- aria2c
- bash
- exiv2
- ffmpeg
- jq
- streamlink
- youtube-dl
- yq (python-yq)

**be sure to update youtube-dl every time since youtube is changing alot meanwhile**

**be sure to install newest ffmpeg if you're using centos 7 'cause the default one fails with youtube opus integration**

Tested on CentOS 7.

## Usage

Run `./live-dl` without any parameter to print help message.

You can run this script in background:

**you should run with ./live-dl --init to add to alias first**

```shell
# Start process
nohup bash live-dl https://www.youtube.com/channel/UC1opHUrw8rvnsadT-iGp7Cg &>/tmp/live-dl-minatoaqua.log &
```
or to debug 
```shell
./live-dl --debug https://www.youtube.com/channel/UC1opHUrw8rvnsadT-iGp7Cg
```

```shell
# View processes
ps aux | grep live-dl
501 94552   964   0  9:38PM ttys009    0:00.06 bash live-dl https://www.youtube.com/channel/UC1opHUrw8rvnsadT-iGp7Cg
501 94765   964   0  9:39PM ttys009    0:00.00 grep live-dl

# Stop process
kill 94552
```

## License

AGPL-3.0
