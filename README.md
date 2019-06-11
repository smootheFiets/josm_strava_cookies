# josm_strava_cookies
Utility for setting Strava cookies in JOSM preferences. This allows to get a high resolution [Strava Heatmap](https://www.strava.com/heatmap).

## Requirements
- python 2 is required. The pre-installed version that comes with macOS works properly.
- Currently, only macOS and the Safari browser are supported.

## Usage
1. Browse to the [Strava Heatmap](https://www.strava.com/heatmap) and setup a Strava account.
2. Log in with your Strava credentials, flagging the *remember me* checkbox. Move the map and zoom in and out, in order to be sure to get the needed cookies.
3. In JOSM preferences, activate the Strava imagery URLs that you need.
4. Change each default imagery URL string from e.g.:
```
tms[3,11]:https://heatmap-external-{switch:a,b,c}.strava.com/tiles/run/bluered/{zoom}/{x}/{y}.png
```
to:
```
tms[3,15]:https://heatmap-external-{switch:a,b,c}.strava.com/tiles-auth/run/bluered/{zoom}/{x}/{y}.png
```
5. Close JOSM.
6. Grant Terminal with full disk access (macOS System Preferences > Security & Privacy > Privacy > Full Disk Access > Add the Terminal application).
7. From the command line run `$ python josm_strava_prefs_upd.py`
8. The imagery URL should be updated to:
```
tms[3,15]:https://heatmap-external-{switch:a,b,c}.strava.com/tiles-auth/run/bluered/{zoom}/{x}/{y}.png?Key-Pair-Id=<YOUR_KEY_PAIR_ID_COOKIE_VALUE>&Policy=<YOUR_POLICY_COOKIE_VALUE>&Signature=<YOUR_SIGNATURE_COOKIE_VALUE>
```

## Licence
- `josm_strava_cookies` is distributed under the GPL v3.0.
- `BinaryCookieReader.py` is distributed under the ...
http://www.securitylearn.net/2012/10/27/cookies-binarycookies-reader/
