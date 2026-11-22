# Changelog

## 14.0-beta22
Shared speakers and headphones play beside your other programs.

**Improvements**
- Settings › Devices & Sharing: every shared device has an Exclusive (bit-perfect) switch. Speakers and headphones now go through the computer's mixer by default, so a game or a call keeps its sound while a Core plays; a DAC stays exclusive and bit-perfect.
- A shared device lets the computer have it back 3 seconds after the music ends.

**Fixes**
- Windows: a headset plugged into another USB port keeps its share instead of being shared a second time, and switching a device off always stops it.
- Home Assistant, Umbrel and Docker: the library no longer reads the same folder again every few seconds.
