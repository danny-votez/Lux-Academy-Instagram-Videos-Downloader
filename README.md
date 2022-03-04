### Lux-Academy Instagram Videos Downloader
- The aim is using Python for creating an application that downloads images and videos from Instagram

#### Python Script
### Import key packages/libraries

```py
from cgitb import text
from email import message
from math import ceil
from tkinter import *
from turtle import left, screensize
from wsgiref import headers
from PIL import ImageTk, Image
import tkinter.font as font
from tkinter import messagebox
from instascrape import Reel
import time

from click import command

```
#  Creating the function for Download Button

```py
def download_function(link):
       try:
              if link:
                     SESSIONID = "69114%3AzFioyrpgP%3A15"  # Enter session below, this is an example
                     headers = {
                            "User-Agent" : "Mozilla/5.0 (Windows NT 10.0; Win64; x64)\
                                   AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.74 \
                                   Safari/537.36 Edg/79.0.309.43",
                            "cookie" : f'sessionId = {SESSIONID}'
                     }
                     google_reel = Reel(link)
                     google_reel.scrape(headers= headers)
                     google_reel.download(fp = f".\\reel{int(time.time())}.mp4")
                     messagebox.showinfo("status", "Reel Downloaded Successfully")
              else:
                     messagebox.showinfo("Empty Field", "Please  Enter the Link")
       except Exception as e :
              messagebox.showinfo("Error!!!!", "Something went wrong. Please Try Again Later.")
              print(e)

```
# Creating the User Interface
```py
root = Tk()
root.title("Instagram Reel Downloader App")
root.minsize(680, 500)
root.maxsize(680, 500)
HEIGHT = 500
WIDTH = 680
times_new = "Times New Roman"
FONT = font.Font(family=times_new, size="18", weight="bold")

canvas = Canvas(root, height=HEIGHT, width=WIDTH)
canvas.pack()

frame = Frame(root, bg="white")
frame.place(relwidth=1, relheight=1)


# Background image with folder to image link

background_image = ImageTk.PhotoImage(Image.open(r"E:\images\backimage.jpg"))   # Image path will be given here
background_label = Label(frame, image = background_image)
background_label.place(relx=-0.35, relwidth=0.7, relheight=1)

label = Label(frame, text = "Download Instagram Reel", font = FONT, bd=5, fg="#0d1137")
label.place(relx=8.48, rely=0.1, relheight=0.1)

FONT = font.Font(family=times_new, size="12", weight="bold")
label2 = Label(frame, text="Enter Link Address : ", font= FONT, bd=5, fg="#e52165")
label2.place(relx=0.48, rely=0.25, relheight=0.1)

entry = Entry(frame, font = FONT, fg="#fbad50")
entry.place(relx=0.48, rely=0.35, relwidth=0.4, relheight=0.05)

# Function to enable dowload will be in the button below

button1 = Button(root, text = "Click to Download", font = FONT, bg="pink", fg="black",
 activeforeground="pink",  activebackground="black", justify="center",
  command=lambda:download_function(entry.get()))

button1.place(relx=0.48, rely=0.45, relwidth=0.2, relheight=0.08)



label2 = Label(frame, text = "Use Instructions: ", font =FONT, bd=5, fg="black", bg="white")
label2.place(relx=0.48, rely=0.6, relheight=0.1)

FONT = font.Font(family=times_new, size="10", weight="bold")
TEXT = " 1. Only Public Account Reels can be Downloaded\n "\
       "2. Enter the Link Address of Reel Above from Instagram"
label2 = Label(frame, text = TEXT, font = FONT, bd=5, fg="blue", justify="left", bg="white")
label2.place(relx=0.48, rely=0.7, relheight=0.1)


root.mainloop()
```

#### Interface Outlook

<img height="400" width="400" src="https://user-images.githubusercontent.com/77758884/156816086-9b11ef1a-f4f9-48e6-b14a-eea1dae04549.png">

#### Use Instructions
- Copy link from instagram
- Paste into "*Enter Link Adress Section*"
- Then "*Click to Download*"
-
#### Extra Resources
- Project builds on key Python concepts from data structures, control structures and reliance on 3rd party modules/libraries
- You can explore more online at [Python 101: Ultimate Python Guide](https://medium.com/@dannyvotez/python-101-ultimate-python-guide-72f1850c9f01) and other online resources
