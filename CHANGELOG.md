# Changelog

## V2.97

* python3-icmplib in Bookworm is too old (V2 vs required V3 which supports host.jitter)
  * Always use pip3 icmplib, which is now installed into a venv: /root/.imon-venv
  * Affects: imon-install, imon@.service
* Correct typo in imon

## V2.96

* Use python3-icmplib on Bookworm
* Eliminate python deprecation messages

## V2.95

* Code cleanup
* When interface newly detected as offline, delete its default route

## V2.90

* Initial version
