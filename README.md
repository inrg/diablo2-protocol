# diablo2-protocol
[![NPM version](https://img.shields.io/npm/v/diablo2-protocol.svg)](http://npmjs.com/package/diablo2-protocol)
[![Build Status](https://img.shields.io/circleci/project/MephisTools/diablo2-protocol/master.svg)](https://circleci.com/gh/MephisTools/diablo2-protocol)


Network protocol for diablo 2 : create client and servers for diablo 1.13 and 1.14.

[Usage example](https://www.youtube.com/watch?v=KYPTijLiwMI&feature=youtu.be)



## Installation

```
npm install diablo2-protocol
```

## Usage

Follow bot in a few lines

```js
const { createClientDiablo } = require('diablo2-protocol')

async function start () {
  const clientDiablo = await createClientDiablo({
    host: 'battlenetip',
    username: 'myuser',
    password: 'mypassword',
    version: '1.14'
  })
  clientDiablo.on('D2GS_PLAYERMOVE', ({ targetX, targetY }) => {
    clientDiablo.write('D2GS_RUNTOLOCATION', {
      x: targetX,
      y: targetY
    })
  })

  await clientDiablo.selectCharacter('mycharacter')
  await clientDiablo.createGame('mygame', '', '21', 0)
  console.log('Has joined the game')
}

start()

```

See docs/API.md

Follow bot example

```
node examples/simpleBot.js [-h] [-v] -au USERNAME -ap PASSWORD -c CHARACTER -gn
                    GAMENAME -gp GAMEPASSWORD -gs GAMESERVER -s SIDSERVER
                    [-dv DIABLOVERSION] -k1 KEYCLASSIC -k2 KEYEXTENSION
```

Sniffer (Linux / MacOS only)

```
cd example/sniffer
npm install
sudo node sniffer.js
```

## Projects using diablo-protocol

* [diablo2-live-viewer](https://github.com/MephisTools/diablo2-live-viewer) displaying a live diablo map and live packets table
* [AutoTathamet](https://github.com/MephisTools/AutoTathamet) Create Diablo2 bots with a powerful, stable, and high level JavaScript API.


## Roadmap
- [ ] Test all packets
- [x] Sniffer
- [x] more documentation
- [ ] Proxy ?
- [ ] More examples
- [ ] Web / mobile interface

## Docs

### Diablo

* doc of diablo2 implementations https://github.com/MephisTools/diablo2-protocol/wiki/Diablo-2-implementations-and-docs
* packets general description http://www.blizzhackers.cc/viewtopic.php?f=182&t=444264
* dump of a normal connection sequence http://www.blizzhackers.cc/viewtopic.php?t=406445
* index of packets https://bnetdocs.org/packet/index
* example of packet doc https://bnetdocs.org/packet/146
* basic example of packet parsing in python of a diablo2 packet https://gist.github.com/rom1504/8d2824d9d89dbd8b991b102696a1321e

### Libs

* node basic client implementation https://nodejs.org/api/net.html#net_net_createconnection_options_connectlistener
* protodef js implementation doc https://github.com/ProtoDef-io/node-protodef https://github.com/ProtoDef-io/node-protodef/blob/master/doc/api.md and https://github.com/ProtoDef-io/node-protodef/blob/master/example.js
* protodef types https://github.com/ProtoDef-io/ProtoDef/blob/master/doc/datatypes.md
* nodepcap for sniffing https://github.com/node-pcap/node_pcap