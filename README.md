# blurt

Application to allow a user to blur moving targets in a video.

More of a proof of concept as there's still a lot to do but the happy path works.

* User uploads video
* Some processing happens on the video to prepare it for the "workbench" (ffmpeg via Python)
* User uses workbench (vue.js) to select where on the video they want to add a blur. They can scroll through it selecting blurs at different keyframes so that a target can be tracked through the video
* Blurring data is uploaded
* Job gets picked up by a batch runner which runs another Python script which makes use of ffmpeg to apply blurring
* Frontend polls until completion
* File downloaded

In theory it should scale well as the various media processing jobs can just increased either with more goroutines or even extra runtimes.
