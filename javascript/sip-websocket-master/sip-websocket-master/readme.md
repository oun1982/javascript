# README

This is a simple SIP implementation with WebSocket as available transport. This project is a fork from [sip.js](https://github.com/kirm/sip.js)

## Installation

1. Clone this project. `git clone git://github.com/bokuwakyuu/sip-websocket.git`
2. Install dependencies. `npm install`

## Usage

By putting http server to initialization option will enable sip server to listen to websocket request on port defined by http server.

    var http = require('http');
    var sip = require('sip-websocket');

    var server = http.createServer(function(request, response) {
        console.log((new Date()) + ' Received request for ' + request.url);
        response.writeHead(404);
        response.end();
    });

    server.listen(8080, function() {
        console.log((new Date()) + ' Server is listening on port 8080');
    });

    sip.start({ websocket : server }, function(request) {});

You could also use [express](https://github.com/visionmedia/express) framework.

    var express = require('express');
    var app = express.createServer();

    app.listen(8080, , function() {
        console.log((new Date()) + ' Server is listening on port 8080');
    });

    sip.start({ websocket : server }, function(request) {});

## Thanks to

* [kirm](https://github.com/kirm) for creating sip.js
* [Worlize](https://github.com/Worlize) for creating WebSocket-Node

## License

See LICENSE