import time
from threading import Thread, Lock
import sys

lock = Lock()

def animate_text(text, delay=0.1):
    with lock:
        for char in text:
            sys.stdout.write(char)
            sys.stdout.flush()
            time.sleep(delay)
        print()

def sing_lyric(lyric, delay, speed):
    time.sleep(delay)
    animate_text(lyric, speed)

def sing_song():
    lyrics = [
        ("Maybe I'd change for you someday", 0.14),
        ("But I can't help the way I feel", 0.14),
        ("Wish I was good", 0.15),
        ("Wish that I could", 0.15),
        ("give you my love now", 0.14),
        ("But I need to", 0.18),
        ("tell you something", 0.18),
        ("My heart just can't be faithful for long", 0.18),
        ("I swear I'll only make you cry", 0.25),
     
    ]
    delays = [0.3, 5.0, 10.0, 15.0, 20.3, 25.0, 27.0, 30.2, 33.3]
    
    threads = []
    for i in range(len(lyrics)):
        lyric, speed = lyrics[i]
        t = Thread(target=sing_lyric, args=(lyric, delays[i], speed))
        threads.append(t)
        t.start()
    
    for thread in threads:
        thread.join()

if __name__ == "__main__":
    sing_song()
