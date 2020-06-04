<!-- TITLE: Modems -->
<!-- SUBTITLE: A quick summary of Modems -->

# Turning wavs to bytes.
nc mooodem.challenges.ooo 5000 | sox -r 48k -t f32 - -t wav - | minimodem -f /dev/stdin 1200