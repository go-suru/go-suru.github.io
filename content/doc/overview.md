+++
title = "Overview"
slug = "overview"
description = "Design Fundamentals"
date = "2020-01-13"
thumbnail = "images/suru-logo.png"
image = "images/suru-logo.png"
author = "Bodie Solomon"
draft = false 
+++

# Suru Design Overview

The design of Suru is focused on 3 main areas:

- [Connect](#connect)
- [Collab](#collab)
- [Decentralize](#decentralize)

This document covers each at a high level.  See
[Implementation Status](#implementation-status) for current progress.

[TODO]: # (or
[install Suru](../getting-suru) and join the Suru pub channel on
[Suru Core](suru-core).
)

## Connect

Suru aims to make it easy to join others on a project and get things
flowing.  If you don't think that's the case, please open a design issue
at [Suru Issues](https://github.com/go-suru/suru/issues/new) labeled
"design".  We ❤️ feedback.

Suru can be used in three modes: private, org, and public.  In Private
mode, nobody else can see your projects or talk to you, and Suru won't
be online or communicate with other computers.

In Org mode, Suru lets you discover and connect to other users who have
invitations to your Suru org.  To invite others to your org, you'll need
to send them a single-use invite link.

In Public mode, you can publish your Suru project URL and anyone can
join.  Public projects can be set up to allow read-only mode by users
who aren't admins.

## Collab

Collab in Suru is focused on Topics.  Within a Topic, peers can chat,
create and discuss items in the Workshop, open Issues, create Schedule
items, and view Worklogs.

[TODO]: # (Make some screencasts of this working.)

## Decentralize

Suru is built from the ground up to be peer-to-peer, using
[libp2p](https://libp2p.io).  All data, such as chat, Topic metadata,
tasks, and so on, is transmitted directly between peers, over encrypted
channels, and data stored for later use is also securely encrypted.

Suru generates a unique cryptographic key pair for network identity and
encryption.

There are two main routes by which data is secured and transmitted: the
Tracker and live channels.

### Peer Tracker

When a Suru node first wants to join a network, it looks up a mapping of
peers in the network from a named Tracker, either using a regular IP
transport or Tor.

The Tor method uses a bundled copy of Tor as a child process and
configures it automatically to look up the Tracker on the given onion
service.

A user can optionally also connect directly to a peer if they know the
peer's address, bypassing the Tracker.  Trackers are meant to maintain a
trustworthy list of reliable network nodes.

Users can host their own Trackers using Suru, or use publicly available
Trackers.

### Live Channels

Once a Suru node joins a network, it hails its peers, publishing its ID
and public key to nodes it is connected to, and discovering other live
peers.  Suru nodes periodically notify one another of their aliveness,
and propagate changes in the network to their connected peers.

Suru nodes may also notify one another of changes in their Topics, Topic
state, or other message queue states, such as chats.

## Implementation Status

### Fundamentals

#### Command-line client

- [ ] id
- [ ] topic
- [ ] live
- [ ] serve
- [ ] pub
- [ ] sub

### Connect

- [ ] Generate ID keypair
- [ ] Private mode
- [ ] Org mode
- [ ] Public mode

### Collab

- [ ] Chat
- [ ] Profile
- [ ] Workshop
- [ ] Issues
- [ ] Schedule
- [ ] Worklog

### Decentralize

- [ ] Tracker (IP)
- [ ] Tracker (Tor)
- [ ] Tracker (Peer)
- [ ] Locate peer
- [ ] Connect to peer
- [ ] Update peer
- [ ] Forward peer update