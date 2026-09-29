---
layout: post
title: "Orbitals returns: old dots, new Android, and a little help from Codex"
excerpt: "Revisiting a 2012 live wallpaper with Codex and Android 16: loading dots, trefoil knots, local settings and no analytics."
date: 2026-09-27 12:00:00 +0000
categories: article
title-image: no_image.svg
---

*A development update, not a new store-release announcement.*

Orbitals started with a fairly modest ambition. Make some dots move around the screen in an interesting way. Touch the screen, disturb the pattern, and watch it settle into something else.

Fourteen years later, the dots still appeal to me. The Android project around them needed rather more attention.

This September I've been revisiting Orbitals with help from Codex. The work has been about getting an old app building and behaving on current Android, without throwing away the little mathematical toy that made it worth writing in the first place.

![Enlarged screenshot details of the pink Trefoil knot pattern and multicoloured Chasing dots on black.]({{ '/assets/images/orbitals-revival/orbitals-showcase.png' | relative_url }})

*Real Android 16 emulator captures from the revived Orbital_LWP app. These are enlarged crops, not concept art. The full screenshots below show the original, much smaller dot scale.*

## Before Orbitals had its own app

The trail starts with Target Live Wallpaper. In [February 2012]({% post_url 2012-02-29-these-messes-i-in-and-out-of %}), I was writing about fireworks, custom models and the usual collection of unfinished Android experiments. Near the bottom of that post was a small addition: "Also just added 'orbitals'".

By [3 May 2012]({% post_url 2012-05-03-announcing-first-release-of-orbitals %}), it had become a separate release. I described Orbitals as the second spin-off from Target Live Wallpaper.

The inspirations were quite specific. Windows 8's loading bubbles suggested the chasing dots. Ordinary orbits supplied the simpler patterns, and the trefoil knot inspired the knotted ones. Ubuntu, XDA and Slashdot were among the references for the tech and open-source colour schemes.

There was no astronomy simulation hiding underneath. This was an excuse to play with motion, colour and a few equations. In the original release, touching the screen changed the randomised colour scheme, trail length and speed.

In [August 2012]({% post_url 2012-08-19-orbitals-and-adb %}), I wrote about fixing some "shifty maths" and separating the transition away from an orbit from the transition back. That let the dots make interesting patterns between the settled ones. The movement between shapes was becoming part of the fun.

## A small naming tangle

There are two related repositories in this story. [Orbital-Live-Wallpaper](https://github.com/PuZZleDucK/Orbital-Live-Wallpaper) holds the original 2012 app. [Orbital_LWP](https://github.com/PuZZleDucK/Orbital_LWP) has its own Android package identity and a later Android Studio history, including settings fixes from 2015.

Both received modernisation work on 22 September 2026. They are related, but they are not interchangeable builds. The screenshots in this post show Orbital_LWP, which retains six orbital patterns, nine palettes and its red-arc widget.

## What the Codex-assisted revival actually changed

Getting a successful build was the first job. Both projects now target Android 16, API 36, with modern Gradle tooling, Java 17 source compatibility and AndroidX. But a fresh build alone would have left plenty of old assumptions intact.

A live wallpaper can have more than one engine. Android may be showing a preview while another instance is active. Each engine now owns its animation state, rather than letting a preview interfere with another instance. Animation callbacks stop when the wallpaper is hidden or its surface disappears, and listeners are removed when the engine is destroyed.

Settings also needed to do what they said. In the original app, placeholder switches became working touch-follow and orbit-transition controls. In Orbital_LWP, the work repaired ignored direction and transition-speed settings, preference loading on a cold start, and mismatched colour labels. Existing preference keys and palette values were preserved.

The surrounding screens received day and night themes and system-bar insets. Widget configuration now starts from cancellation, so backing out does not accidentally create a widget. The widgets remain static; there is no reason to keep waking up a background task to redraw an unchanging image.

That is the useful part of this Codex-assisted return for me. It made it practical to revisit the build, lifecycle code and tests around an old experiment, while keeping the original orbit formulas and visual character.

## A look at the revived app

<figure class="post-screenshots">
  <div class="screenshot-pair">
  <a href="{{ '/assets/images/orbitals-revival/trefoil-1.png' | relative_url }}"><img src="{{ '/assets/images/orbitals-revival/trefoil-1.png' | relative_url }}" alt="Full Android wallpaper preview showing small pink and magenta Trefoil dots against black." width="1080" height="2400" loading="lazy"></a>
  <a href="{{ '/assets/images/orbitals-revival/chasing-preview.png' | relative_url }}"><img src="{{ '/assets/images/orbitals-revival/chasing-preview.png' | relative_url }}" alt="Full Android wallpaper preview showing a short trail of coloured Chasing dots." width="1080" height="2400" loading="lazy"></a>
  </div>
  <figcaption>Trefoil and Chasing in Android's system wallpaper preview. The original pixel-sized dots look small on a dense display. These captures show previews, not a newly applied home-screen wallpaper.</figcaption>
</figure>

<figure class="post-screenshots">
  <div class="screenshot-pair">
  <a href="{{ '/assets/images/orbitals-revival/trefoil-settings.png' | relative_url }}"><img src="{{ '/assets/images/orbitals-revival/trefoil-settings.png' | relative_url }}" alt="Orbital settings for pattern, speed, direction, dot colours, size, count and transitions." width="1080" height="2400" loading="lazy"></a>
  <a href="{{ '/assets/images/orbitals-revival/widget-two.png' | relative_url }}"><img src="{{ '/assets/images/orbitals-revival/widget-two.png' | relative_url }}" alt="Android emulator home screen with two static red-arc Orbital widgets." width="1080" height="2400" loading="lazy"></a>
  </div>
  <figcaption>The restored settings screen and two launcher-hosted red-arc widgets. The widgets are static images, not additional animated wallpapers.</figcaption>
</figure>

## Tested, with a few limits

The original app's revival records five passing instrumentation tests on an Android 16 phone, plus manual preview, touch and settings checks. Orbital_LWP records six Android 16 instrumentation tests, five JVM tests and seven compatibility contracts containing 48 assertions. A separate review reran the local contracts, unit tests and lint, and inspected the saved device evidence.

Those checks matter more than a claim that the app is simply "modern". They cover things such as settings surviving recreation, real wallpaper-engine callbacks, and widget configuration behaving properly.

They do not establish long-term battery performance or compatibility with every Android release. Android 6 runtime support remains untested. The original dot sizing and low-resolution static widget artwork also remain visible reminders of the app's age. The revival is working development code, not a claim that a new store release has shipped.

## Privacy and local app data

**No accounts, advertising or usage analytics.** The two development builds described here do not include a service that collects wallpaper-user data for PuZZleDucK, and neither requests internet access. They do not send us personal information, advertising identifiers, location or a history of your touches.

Touch input drives the animation while you use it. It is not kept as an interaction history.

The apps do save configuration on your device, such as your chosen pattern, colours and speed. Those settings are still data: they let the wallpaper remember how you set it up, but they are not tracking records and we do not receive them.

There is no developer-operated database of wallpaper users to retain, sell or share. Local settings normally remain until you clear the app's storage or uninstall it. Both current builds allow Android backup, so your device or backup provider may preserve and restore settings. Uninstalling does not promise deletion of an Android-managed backup; use your device's backup controls for those copies. [Android's backup documentation](https://developer.android.com/identity/data/autobackup) explains this separate system behaviour.

This statement covers the September 2026 development versions discussed here: Orbital Live Wallpaper 2.1 (`orbitlivewallpaperfree.puzzleduck.com`) and Orbital_LWP 2.0 (`org.puzzleduck.orbital_lwp`). If you follow an external link, the browser, app store or other service has its own privacy policy.

For questions, [email PuZZleDucK](mailto:{{ site.email }}). Any message you choose to send is separate from the apps' operation and is handled through the email service.

## Back to the dots

The appeal is still the same as it was in 2012. A few coloured dots follow a pattern, a touch sends them somewhere else, and the screen becomes a small experiment in motion again.

It is good to have the code moving too.
