# video volume increase
```Python
from pydub import AudioSegment
from pytube import YouTube

yt = YouTube('https://www.youtube.com/watch?v=9bmO4LUSAuA&ab_channel=PyWaw').streams.first().download()
target = -17
audio = AudioSegment.from_file(yt, format='mp4')
avg = audio.dBFS
if avg < target:
    audio = audio + (target - avg)
audio.export(yt, format="mp4")
print(audio.dBFS)
