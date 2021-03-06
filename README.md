OpenWebRX
=========

OpenWebRX is a multi-user SDR receiver software with a web interface.

![OpenWebRX](http://blog.sdr.hu/images/openwebrx/screenshot.png)

It has the following features:

- [csdr](https://github.com/jketterl/csdr) based demodulators (AM/FM/SSB/CW/BPSK31/BPSK63)
- filter passband can be set from GUI
- it extensively uses HTML5 features like WebSocket, Web Audio API, and Canvas
- it works in Google Chrome, Chromium and Mozilla Firefox
- currently supports RTL-SDR, HackRF, SDRplay, AirSpy, LimeSDR, PlutoSDR
- Multiple SDR devices can be used simultaneously
- [digiham](https://github.com/jketterl/digiham) based demodularors (DMR, YSF, Pocsag)
- [dsd](https://github.com/f4exb/dsdcc) based demodulators (D-Star, NXDN)
- [wsjt-x](https://physics.princeton.edu/pulsar/k1jt/wsjtx.html) based demodulators (FT8, FT4, WSPR, JT65, JT9)

## Setup

### Raspberry Pi SD Card Images

Probably the quickest way to get started is to download the latest Raspberry Pi SD Card Image. It contains all the
depencencies out of the box, and should work on all Raspberry Pis. It is based off the Raspbian Lite distribution,
so [their installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/) apply.

You can find the latest images [here](https://s3.eu-central-1.amazonaws.com/de.dd5jfk.openwebrx/index.html). You can
also checkout the `nightly` folder, which has the most recent builds, albeit untested.

Once you have booted a Raspberry with the SD Card, it will appear in your network with the hostname "openwebrx", which
should make it available as https://openwebrx/ on most networks. This may vary depending on your specific setup.

For Digital voice, the minimum requirement right now seems to be a Rasbperry Pi 3B+. I would like to work on optimizing
this for lower specs, but at this point I am not sure how much can be done. 

### Docker Images

For those familiar with docker, I am providing
[recent builds and Releases for both x86 and arm processors on the Docker hub](https://hub.docker.com/r/jketterl/openwebrx).
You can find a short introduction there.

### Manual Installation

OpenWebRX currently requires Linux and python >= 3.6 to run. 

First you will need to install the dependencies:

- [csdr](https://github.com/jketterl/csdr)
- [rtl-sdr](http://sdr.osmocom.org/trac/wiki/rtl-sdr)
- [owrx_connector](https://github.com/jketterl/owrx_connector)

Optional dependencies if you want to be able to listen do digital voice:

- [digiham](https://github.com/jketterl/digiham)
- [dsd](https://github.com/f4exb/dsdcc)

Optional dependency if you want to decode WSJT-X modes:

- [wsjt-x](https://physics.princeton.edu/pulsar/k1jt/wsjtx.html)

[Detailed installation instructions in the Wiki](https://github.com/jketterl/openwebrx/wiki/Manual-Package-installation-(including-digital-voice))

After cloning this repository and connecting an RTL-SDR dongle to your computer, you can run the server:

	./openwebrx.py
	
You can now open the GUI at <a href="http://localhost:8073">http://localhost:8073</a>.

Now the next step is to customize the parameters of your server in `config_webrx.py`.

Actually, if you do something cool with OpenWebRX, please drop me a mail:  
*Jakob Ketterl, DD5JFK &lt;dd5jfk@darc.de&gt;*

## Usage tips

You can zoom the waterfall display by the mouse wheel. You can also drag the waterfall to pan across it.

The filter envelope can be dragged at its ends and moved around to set the passband.

However, if you hold down the shift key, you can drag the center line (BFO) or the whole passband (PBS).

## Licensing

OpenWebRX is available under Affero GPL v3 license
([summary](https://tldrlegal.com/license/gnu-affero-general-public-license-v3-(agpl-3.0)).

OpenWebRX is also available under a commercial license on request. Please contact me at the address
*&lt;randras@sdr.hu&gt;* for licensing options. 
