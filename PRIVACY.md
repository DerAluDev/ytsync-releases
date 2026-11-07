# Privacy Policy – YouTube Watch Sync

_Last updated: 2026-11-07_

YouTube Watch Sync ("the extension") keeps YouTube playback in sync between people who join the same room. It has no accounts, no analytics, no ads and no tracking.

## What the extension sends, and where

| Data | Sent to | Why |
|---|---|---|
| Room identifier (a SHA-256 hash of the room code; the code itself never leaves your browser) | Signaling relay (`squadfob.de`, path `/ytsync/ws`) | Introduce the people in one room to each other |
| Connection setup data (WebRTC offers/answers, ICE candidates, which contain your IP address), authenticated with a key derived from the room code | Signaling relay, then the other room members | Establish direct peer-to-peer connections |
| Your IP address (STUN requests) | STUN servers: `stun.l.google.com` (Google) and `stun.cloudflare.com` (Cloudflare) by default | Discover your public address for peer-to-peer connections. You can change or remove these in the popup settings. |
| Display name, current video ID, play/pause/seek/speed state, ad status | Other members of your room, directly over WebRTC data channels. **Not** through the relay. | The core sync feature |

Room members can see each other's IP addresses, which is inherent to WebRTC.

## What the relay does with it

The relay forwards connection-setup messages between members of a room and keeps them only in memory while the room is active. It does not store messages, display names, video IDs or playback state, and has no database. The relay's own code does not write request logs. The reverse proxy in front of it may keep standard access logs (IP address, timestamp) for security and abuse prevention for up to 30 days. The relay's source code is in this repository (`server/`).

## What is stored on your device

Your settings (display name, relay URL, ICE servers) are in extension storage. The active room is kept in session storage for the browser tab and is cleared when you leave the room or close the tab. Nothing is stored remotely.

## Sharing

Data is shared only as listed above. We do not sell data or use it for advertising, profiling or analytics. Google and Cloudflare handle STUN requests under their own privacy policies.

## Your control

Leave a room at any time from the popup. You can change the relay and ICE/STUN servers in the popup settings (including self-hosting the relay), or uninstall the extension.

## Contact

Questions: CONTACT_EMAIL_HERE
