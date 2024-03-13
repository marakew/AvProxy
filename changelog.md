
## v2.26
	- add HLS segment duration and idr limit, options are AppleDuration and AppleIDRLimit
	  values in milliseconds
	- improve live stats and add IDR average and IDR lists of last 20 IDR frames

## v2.25
	- add parse Maximum Bitrate descriptor
	- reimplement segment split by segments, pass only AVC,HEVC,AAC
	- rollback segment name as numbers instead md5 hash, for improve speed

## v2.24
	- sync free public with commerce version except commerce features
	git repo flushed from old binary
	build linux AvProxy-x64
	build windows AvProxy-x64.exe
	contact me if you need build for other architecture

## v2.19.2
	- fix TsPush by IFace
	build linux AvProxy-x64, contact to me for build fix for another binary

## v2.19.1
	- fix ApplePreroll/AppleReserve options
	build linux AvProxy-x64, contact to me for build fix for another binary

## v2.24
	- improve hls aes encryption/decryption speed, using hw if avail
	- fix hls encryption memory corruption, rare case
	- add config option for hls output, chunk count and chunk reserve
	- improve using 'poll' instead 'select' for linux
	nobuild

## v2.23
	- T2MI(PLP) demux for inputs
	nobuild

## v2.22
	- windows build x32/x64
	- add accept4 for linux
	- improve hls client download segments
	- improve http/hls roundrobin requests for multi records DNS
	- fix crash while pat/pmt changes on stream
	nobuild

## v2.21
	- add RTSP interleave input
	- http "Server:" response
	- fix handle some MPEGTS desc
	- SCTE-35 stream detect
	nobuild

## v2.20
	- pass Spu stream
	- keep origin url for reconnect while redirect 30x
	- improve detect hls segment
	- setup User-Agent from config
	- "kill -SIGUSR1 pid" - for reload local/remote config
	- fix handle std::exception
	nobuild

## v2.19
	- pass HEVC stream

## v2.18
	- there is no need Name for input

## v2.17
	- AvProxy.xml format changed
	- add MPTS demux for input
	
## v2.16
	- add AES-128 method for hls output
	- fix HLS refetch playlist if no segment
	- stop play HLS if ENDLIST

## v2.15
	- add AES-128 method for hls input
	- fix HLS, don't fetch segment often than segment duration

## v2.14
	- improve hls variant for choose BANDWIDTH
	  default bandwidth in config xml Bandwidth=number in kpbs
	  apple hls uses bps in m3u8 variant, 1 bps=1000 kbps in this case
	  report bandwidth to trace
## v2.13
	- add https for output
	  available options -ssl_port, -ssl_cert, -ssl_cert_key, -ssl_cert_key_pass
	  there is only one service port available http or https

## v2.12
	- add http basic and digest authorization on http/m3u8 input
	  http://username:password@hosname/path
	  or
	  m3u8://username:password@hosname/path
	- add https secure socket layer for http/m3u8 input
	  https://hostname/path or m3u8s://hostname/path

## v2.11
	- add xml error message and line,pos of error
	- add simple vod, -VodDir /cache/
	  and access through http://ip/vod/playlist.m3u8 to get playlist of all file in /cache/ dir
	- change Apple to live path http://ip/live/playlist.m3u8 to get all entries

## v2.10
	- add PCR DTS PTS trace info
	no build

## v2.09
	- add UDP/RTP push target

	example config

	<Entry Name="test" Url="http://myhttp.com/play/a02h">
	        <TsPush Url="rtp://192.168.65.132:8888"/>
	        <TsPush Url="udp://192.168.65.134:8888"/>
	        <TsPush Url="rtp://192.168.65.135:8888"/>
	</Entry>

## v2.08
	- fix DATA stream errors
	- static binary without stdc++ depend
	- new cmd opt -Trace to enable trace print in console, by default any trace disable

## v2.07
	- fix http retry url timeout

## v2.06
	- refix M3U8 parser for strange playlist 0D 0A sequence

## v2.05
	- add reply 404 not found if no channel in Apple/
	- fix m3u8 parser for m3u8 prog list

## v2.04
	- reimprove prev fix and include old fix

## v2.03
	- fix memory leak after switch to scramble stream

## v2.02.0
	- fix fast close tcp session

## v2.02
	- add users stat page http://ip/Users/
	- fix PartialContent Ranges: bytes=

## v2.01
	- add tag VERSION:3 to hls
	- add param to change default port -HttpPort 8080 as example
	- add param in xml Entry conf, Desc="name of channel", for publsh name in m3u8 playlist
	- add param for tuning cache of hls storage, for decrise call malloc,free
	  param -AppleCache 50 as example, by default 0 if no cache
	  one number of value eq 200 kb
	- fix descriptor leak when use -ConfigUrl
	- fix generate m3u8 playlist for non default port

## v2.0
	- avail entry with end in url scheme like .htm .m3u8 .txt .ts
	- access by entry without extension will avail as regular http stream non hls
	- correct chunks for hls stream strim by PES start
	- ts chunks name with md5
	- ts chunks allow use Ranges bytes request
	- access by default url got list of all channels