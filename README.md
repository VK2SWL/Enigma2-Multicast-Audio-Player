# Enigma2-Multicast-Audio-Player
Windows companion for Enigma2 receivers: tune a scanned frequency, extract a DVB-MPE PID over SSH, discover RTP/ADTS AAC multicast feeds, play them in VLC, and monitor RCS/UECP metadata.

# What it does

Enigma2 Multicast Audio Player is a Windows companion application for Enigma2 set-top boxes such as Zgemma receivers. It can tune the receiver to a scanned frequency, capture one selected MPEG-TS PID over SSH, extract DVB Multiprotocol Encapsulation (MPE) datagrams, discover RTP multicast audio flows, recover ADTS AAC audio, and make the detected stations available to VLC over local HTTP.

It can also display metadata found alongside the audio, including observed RCS playout metadata and, when present, RDS/UECP carried in RTP header extensions.

The application does not perform decryption or conditional-access processing.

# Main features

Windows GUI for receiver address, frequency and PID.

Reads Enigma2 lamedb v4 and v5 and selects the nearest scanned transponder within 3 MHz.

Uses local OpenWebif on the receiver to zap to a service on the selected transponder.

Streams only the chosen PID from the receiver using dvbsnoop over SSH.

Text-safe transport from receiver to Windows using Base64.

DVB-MPE section reassembly and IPv4/UDP extraction.

Automatic RTP flow discovery; multicast IP, UDP port and RTP payload type do not need to be hard-coded.

ADTS AAC detection even when a short RTP payload prefix is present.

Local per-feed HTTP audio endpoints and an automatically generated VLC playlist.

Automatic VLC launch when AAC is detected.

Uses the normal 64-bit VLC installation and requests a maximized normal VLC window.

Web dashboard at http://127.0.0.1:18100/.

RDS/UECP monitor at http://127.0.0.1:18100/rds when enabled.

Metadata Track Selector so console metadata follows the audio feed selected by the user in VLC.

Optional PID recording to captures/.

No third-party Python packages are required; the Python side uses the standard library.


# Requirements

Windows PC

Windows 10 or Windows 11.

Python 3.8 or newer, with Tkinter. A normal python.org Windows installation is suitable.

Windows OpenSSH Client (ssh.exe).

VLC media player is strongly recommended for playback.

Network access to the Enigma2 receiver on the normal SSH port (22).

Enigma2-based receiver with a working tuner and a scanned service/transponder database.

OpenWebif installed and running.

SSH access for the chosen account; root is the default used by the player.

python3 installed on the receiver.

dvbsnoop installed on the receiver.

Readable /etc/enigma2/lamedb.

The target frequency/transponder must already have been scanned into Enigma2.

The selected PID must carry a format supported by the player (DVB MPE containing compatible RTP/ADTS AAC for audio playback).

For detailed checks and setup notes, see docs/PREREQUISITES.md.

# Quick start

Extract the release ZIP on the Windows PC.

Make sure the Enigma2 box and PC can reach each other over the network.

Double-click START-ENIGMA2-BOX-MULTICAST-PLAYER.cmd.

Enter the receiver IP address or host name.

Enter the desired frequency and target PID.

Enable or disable RDS/UECP decoding and PID recording as required.

Leave Open VLC automatically when audio is detected enabled for the normal workflow.

Click Start Player.

Enter the receiver SSH password in the command window if prompted.

Once compatible AAC feeds are detected, VLC opens with the generated playlist.

Select the desired audio feed in VLC.

Select the matching feed in the Metadata Track Selector to filter the console metadata to that track.

# Legal/use note

This software is intended for lawful reception, analysis and playback of streams that the user is authorised to receive. It contains no conditional-access or decryption functionality. Broadcasters' audio, metadata and recorded transport streams may be subject to copyright or other rights; do not upload captures unless you have permission.
