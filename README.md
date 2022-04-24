# Spotity Speed Chrome Extension
Change the speed of spotify song and video playback.
---
Original version of this forked extension is downloadable from Google Chrome webstore. Get it here: [Chrome extension link](https://chrome.google.com/webstore/detail/spotify-playback-speed-ac/cgbihpjbhpdfbdckcabcniojdhcgblhd)

### Version 1.6:
 - Added title to the speed input, for better visibility.
 - Placed the input into the controls on the new Spotify layout.

---
## Install from github..
+ download project as zip ![preview img](https://i.stack.imgur.com/PrvYK.png)
+ unzip and load the folder as [unpacked extension](https://developer.chrome.com/extensions/getstarted#manifest)
+ remember to click that little refresh button on the extension page for the extension if you make code changes.
---
## The problem this extension solves: 
>  You will gain control over the video/audio element that is hidden and only referenced in spotify's encapsulated code.

## The solution: 
+ The code main part of the code is written in a template literal string with back quotes ---> `
	- This allows a multilined string with double quotes and single quotes without breaking the string variable
	
+ This string named code is injected into the top of the html dom as a script element when the page loads
	- It loads before spotify's scripts and can pre-append the browser's code of `document.createElement` before it's used
	- Whenever spotify's scripts execute `document.createElement('video')` a reference to the element created is stored in VideoElementsMade
		- `document.createElement('video')` used to be an audio element until spotify started supporting videos  and now it's randomly either
+ The `timeout()` loop is just an added assurance that the playbackspeed input element is created and that the speed is changed to the stored speed from previous sessions
