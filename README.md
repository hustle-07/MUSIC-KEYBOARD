# MUSIC-KEYBOARD
import tkinter as tk 
import pygame
from pynput import keyboard
#  for watching this type of content subscribe
# source code in description

pygame.mixer.init()

# sounds
sounds = {
    "a":pygame.mixer.Sound("day-1/MOUNTAIN.WAV"),
    "b":pygame.mixer.Sound("day-1/SLOWED.WAV"),
    "c":pygame.mixer.Sound("day-1/SOUL.WAV"),
    "d":pygame.mixer.Sound("day-1/SCREWEDQUEEN.WAV"),
    "e":pygame.mixer.Sound("day-1/DOLM.WAV"),
    "f":pygame.mixer.Sound("day-1/WATERMELLO.WAV")

}

# PLAYING SOUND
def play_sound(key):
    try:
        k = key.char.lower()
        if k in sounds:
            sounds[k].play()
            label.config(text=f"Key Pressed: {k.upper()} 🎵")

    except:
        pass


# keyboard listener
def on_press(key):
    play_sound(key)

listener = keyboard.Listener(on_press=on_press)
listener.start()

# gui
root = tk.Tk()
root.title("keyboard music instrument")
root.geometry("700x450")
root.configure(bg="black")

title = tk.Label(
root,
text = "🎹 Keyboard Music Instrument",
font=("consolas",24),
fg="lime",
bg="black"    
)
title.pack(pady=20)
label = tk.Label(
root,
text = "Press A B C D E F to play sounds",
font=("consolas",16),
fg="white",
bg="black"
)
label.pack(pady=30)

textbox = tk.Text(root,
font = ("consolas",14),
bg="#111111",
fg = "lime",
insertbackground="lime"
)
textbox.pack(fill="both",expand=True,padx=20,pady=20)
root.mainloop()
