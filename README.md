# Youtube Video Downloader Utility in Python3
![image](https://user-images.githubusercontent.com/73791462/175214418-06341129-1c8f-4675-b4d3-a76caba84369.png)
![image](https://user-images.githubusercontent.com/73791462/175215912-d1b346aa-c990-48bd-9b24-0e26053eb5d6.png)

`````
from os import system
from time import sleep
from pytube import YouTube

def InitDownloader():
    system('clear')
    url=input("[type quit/exit to leave program]Enter Video Url: ")
    if(url.lower()=="quit" or url.lower()=="exit"):
        print("shutting down ...")
        exit()
    yt = YouTube(url=url)
    print(f"title : {yt.title}")
    print(f"Video length : {yt.length/60}m")

    print("Good News Video is Available for Download :)\n")
    print(f"Author: {yt.author}\n---------------\n")
    print(f"Description:\n{yt.description}")

    user_input = input(
        "Would you like to download audio only or Video\n a : audio only\n v : video and audio both\nInput: "
    )
    if (user_input.lower() == 'a'):
        print("downloading audio version...")
        yt.streams.filter(only_audio=True)
        yt.streams.filter(file_extension='mp3')
        stream = yt.streams.get_by_itag(140)
        stream.download()
    elif (user_input.lower() == 'v'):
        print("downloading mp4 version(res: 720p)...")
        yt.streams.filter(file_extension='mp4')
        stream = yt.streams.get_by_itag(22)
        stream.download()

    else:
        print("[Error] : Invalid Input!\nshutting down ...\n")

if(__name__=="__main__"):
    print("Youtube Video Downloader Utility\nCopyright(c)2022 Vishal Ahirwar.\n")
    sleep(3)
    while(True):
        InitDownloader()
else:
    print("Can't Execute!")
`````
