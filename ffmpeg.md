<!-- TITLE: Ffmpeg -->
<!-- SUBTITLE: A quick summary of Ffmpeg -->

# Changing Bitrate
ffmpeg -i <filename> -ar 22050 22050.wav

# Dropping Stereo
ffmpeg -i <filename> -ac 1 mono.wav

