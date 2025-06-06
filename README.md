from moviepy.editor import *

# Load the video
video = VideoFileClip("input_video.mp4")

# Trim the video (e.g., first 10 seconds)
trimmed_video = video.subclip(0, 10)

# Add background music
music = AudioFileClip("background_music.mp3").subclip(0, 10)
final_video = trimmed_video.set_audio(music)

# Add text on the video
txt = TextClip("Hello from MoviePy!", fontsize=50, color='white')
txt = txt.set_pos('center').set_duration(10)
final_with_text = CompositeVideoClip([final_video, txt])

# Export final video
final_with_text.write_videofile("output_video.mp4", fps=24)
