---
layout: post
title: "Mixtape — privacy and data-retention policy"
excerpt: "How Mixtape uses local music, saves tape settings, works with Android media controls and backup, and handles deletion."
date: 2026-10-01 00:00:00 +1000
categories: policy
permalink: /mixtape-privacy-policy/
contact_email: "PuZZleDucK+mixtape@gmail.com"
title-image: mixtape.png
show-title-icon: true
---

This policy covers Mixtape for Android, package `org.puzzleduck.mixtape`.

Mixtape is developed by **PuZZleDucK**. Privacy questions can be sent to [{{ page.contact_email }}](mailto:{{ page.contact_email }}).

## In brief

Mixtape plays music stored on your device. It has no user account, advertising SDK, developer-operated analytics service or automatic upload of your music library. The app does not request Android's internet permission.

The app does access and store some information locally to work. Android media controls and Android-managed backups are separate data flows described below. “No upload to us” does not mean “no data is processed” or “nothing can leave the device”.

## Music and permissions

With your permission, Mixtape reads Android's audio library and opens audio files for playback. It uses track titles, artist and album names, filenames, durations, file types and sizes, track numbers, media identifiers and added/modified dates to organise tapes, display track information and play your music.

Fast-forward and rewind effects decode short portions of those same files locally. They do not record the microphone or upload audio for processing.

- On Android 13 and later, Mixtape asks for access to music and audio.
- On Android 7–12, it uses the older storage-read permission.
- On Android 7–9, a separate storage-write permission is requested if you choose to permanently delete an audio file. Newer Android versions use the relevant system permission or deletion-consent flow.

You can deny or revoke audio access in Android's app-permission settings. Library access and playback of inaccessible files will then be unavailable. Revoking a permission does not itself erase the app's saved tape settings.

The app also uses Android's media-playback service and wake-lock facilities for background playback. Its playback dependencies declare network-state access; this is not permission to send music or other information over the internet.

## Information saved on the device

Mixtape stores app-private preferences for permission-request history, tape names and appearance, handwriting and theme choices, library grouping, filename exclusions, and tape membership. Membership includes media identifiers and identifiers of songs removed from tapes, so a library refresh does not silently add them back.

The app reads audio from its existing location. Creating or editing a virtual tape does not create a new copy of each music file.

Mixtape uses Android's app-private storage protections for its preferences. This is not a promise of protection against someone who has access to an unlocked, rooted or otherwise compromised device.

## Android playback controls and connected systems

Track metadata, the playback queue and playback state are made available through Android's media-session interface. This enables notifications, lock-screen controls and headset or Bluetooth media controls. Mixtape does not provide an Android Auto or Automotive browsing interface.

Those surfaces may show song titles, artists and other media information outside Mixtape's own screen. Their operation and any further processing are controlled by Android and the connected host or service, not a Mixtape server.

## Android backup and device transfers

Mixtape allows Android backup of its saved preferences. Depending on your device and backup settings, Android or your backup provider may copy and later restore that data, including during a device transfer.

These are system-managed copies, not uploads to a server operated by PuZZleDucK. Uninstalling the app does not guarantee removal of an existing backup. See your device's backup controls and [Android's backup documentation](https://developer.android.com/identity/data/autobackup).

## Retention and deletion

- **Saved app data:** preferences and tape membership remain until changed or removed by clearing Mixtape's storage or uninstalling it.
- **Tape edits:** removing a song from a tape or adding an exclusion does not delete the underlying audio file. Resetting tapes is a reshuffle/reset feature, not a complete personal-data erasure tool.
- **Music files:** clearing app storage or uninstalling Mixtape does not delete your shared music collection. The separate **Delete from device** action can permanently remove a selected audio file after confirmation and any required Android permission or consent.
- **Backups:** manage these through Android or the relevant backup provider. App-level deletion does not promise deletion of their copies.
- **Developer accounts:** there is no Mixtape account or developer-hosted music-library database to delete.

## Support messages and external services

If you contact PuZZleDucK, the email address, message and any attachments you choose to send are received through the email provider. They are separate from the app's local-only operation. Please avoid including unnecessary personal information.

External websites, app stores, email providers and connected platform services have their own privacy policies. This statement describes Mixtape itself; it does not make promises on their behalf.

## Changes and questions

We will update this policy when the way Mixtape handles data changes. Questions or requests about information you have voluntarily sent can be directed to [{{ page.contact_email }}](mailto:{{ page.contact_email }}).
