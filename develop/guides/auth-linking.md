# Auth-Linking

## Overview
This document describes the typical flow and API used for registering and linking a device to a video service. The primary and recommended method for linking a device involves 3 main steps:

- (1) Generating a short on-screen registration code on the Roku device.
- (2) Having the user link the device by entering the registration code on the  the provider website.
- (3) Once the device detects that registration is complete, it displays a congratulations screen and allows the user access to the video service.

This is known as the "rendezvous" style of registration.

Several transactions between the device and the provider server make this work.
The steps are linked below, with each number representing one request/response transaction between device and server.

- (1a) First, the device makes a "pre-registration" request to the server.
- (1b) The server generates a short registration code and sets up an entry in a database associating the code with a temporary request for linking.
- (1c) The device receives this response and displays the code to the user.
- (2a) The device begins making a sequence of "link" requests to the server.
- (2b) The server responds to the link request with a "not completed" code until the user successfully enters the code into the web site, or the code expires.  -
- (3a) When the user has successfully entered the code plus any other necessary credentials on the provider web site, the server reassociates the code with the user's real account.
- (4) The next time the device makes a "link" query, the server responds with a permanent token that can be used to access the user's account.

All subsequent API requests use this token to uniquely identify the customer and device. A request can be made as HTTP GET with values in parameters, or HTTP POST with values in the body of the request, for example, as XML or JSON.

## Pre-Registration
