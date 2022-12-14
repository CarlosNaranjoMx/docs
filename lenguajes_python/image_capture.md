- [fun_url_validator.py](#fun_url_validator.py)
- [fun_youtube_url_validation.py](#fun_youtube_url_validation.py)
- [main.py](#main.py)
- [usr_captions.py](#usr_captions.py)
- [usr_capture.py](#usr_capture.py)
- [usr_debug.py](#usr_debug.py)
- [usr_directories.py](#usr_directories.py)
- [usr_download_video.py](#usr_download_video.py)
- [usr_download_youtube.py](#usr_download_youtube.py)
- [usr_image_to_ico.py](#usr_image_to_ico.py)
- [usr_open_window.py](#usr_open_window.py)
- [usr_songs.py](#usr_songs.py)
- [usr_tk.py](#usr_tk.py)
- [usr_tk_obj_list.py](#usr_tk_obj_list.py)
- [usr_write.py](#usr_write.py)
- [__init__.py](#__init__.py)
- [fun_chars.py](#fun_chars.py)
- [fun_database.py](#fun_database.py)
- [fun_dirs.py](#fun_dirs.py)
- [fun_download.py](#fun_download.py)
- [usr_convert_to_image.py](#usr_convert_to_image.py)
- [usr_folder.py](#usr_folder.py)
- [__init__.py](#__init__.py)
# fun_url_validator.py
~~~python
from re import Match, match
# objeto con los folders y las variables (?) constructor ini
def youtube_url_validation(url:str)->Match:
    youtube_regex = (
        r'(https?://)?(www\.)?'
        '(youtube|youtu|youtube-nocookie)\.(com|be)/'
        '(watch\?v=|embed/|v/|.+\?v=)?([^&=%\?]{11})')
    youtube_regex_match = match(youtube_regex, url)
    if youtube_regex_match:
        return youtube_regex_match
    return youtube_regex_match
~~~
# fun_youtube_url_validation.py
~~~python
from re import Match,match
# objeto con los folders y las variables (?) constructor ini
def youtube_url_validation(url:str)->Match:
    youtube_regex = (
        r'(https?://)?(www\.)?'
        '(youtube|youtu|youtube-nocookie)\.(com|be)/'
        '(watch\?v=|embed/|v/|.+\?v=)?([^&=%\?]{11})')
    youtube_regex_match = match(youtube_regex, url)
    if youtube_regex_match:
        return youtube_regex_match
    return youtube_regex_match
~~~
# main.py
~~~python
# from os.path import expanduser,join, exists
# from os import remove, walk, listdir, mkdir
# import json
# import subprocess
# from traceback import print_exc
# from colorama import Fore, Back, Style
# import urllib
# from urllib.parse import urlparse
# from inspect import signature
# from pytube import YouTube,Playlist
# from moviepy.editor import *
# import youtube_dl
# from pytube.exceptions import RegexMatchError
# from youtube_transcript_api import YouTubeTranscriptApi
# from youtube_transcript_api.formatters import JSONFormatter
# from urllib.error import URLError
# from http.client import RemoteDisconnected
# import _thread
# from mss import mss
# from PIL import Image
# from tkinter import *
# from tkinter.ttk import *

# Import classes in python
################################# USER PACKAGES ################################
from usr_tk_obj_list import tk

from usr_capture import *
from usr_write import *
from usr_download_youtube import *
from usr_open_window import *

# Crear objetos de python con los elementos de tkinter

if __name__=="__main__":
    tk.mainloop()
    # execfile("usr_capture.py")
~~~
# usr_captions.py
~~~python
# mejor no guardar las cosas en carpetas
from fun_youtube_url_validation import youtube_url_validation
from fun_download_youtube.fun_chars import valid_chars
from fun_download_youtube.usr_folder import Folder
from usr_directories import CATEGORIA_VIDEOS, create_directories
# other packages
from os.path import join
from youtube_transcript_api import YouTubeTranscriptApi
from colorama import Fore
from pytube import YouTube,Channel
from http.client import RemoteDisconnected
from traceback import print_exc
from youtube_transcript_api._errors import TranscriptsDisabled

debug = True

def all_channel_captions(url:str,categoria:str):
    try:
        channel = Channel(url)
    except RemoteDisconnected: print(Fore.RED,"Error al crear el objeto youtube",Fore.WHITE)
    except Exception: print_exc()
    # title = channel.channel_name
    count = 0
    for video,url in zip(channel.videos,channel.video_urls):
        name = f"{count}_{video.title}"
        try:
            action_download_captions(name=name,categoria=categoria,url=url,captions_folder=CATEGORIA_VIDEOS)
        except TranscriptsDisabled:
            print(Fore.RED,"Error video sin subtitulos",Fore.WHITE)
            print("name:",name)
            continue
        count += 1


# EXAMPLES
# name: The mathematical secrets of Pascalâ€™s triangle - Wajdi Mohamed Ratemi

# directorio en el que se guardara
def action_download_captions(name:str,categoria:str,url:str,captions_folder:str)->None:
    youtube_regex = youtube_url_validation(url)
    url_id = youtube_regex.group(6)
    valid_name = valid_chars(name)

    #creacion de los directorios
    create_directories(join(captions_folder,categoria))
    
    #elementos que deberÃ­an ir en algun objeto
    hard_folder = join(captions_folder,categoria,valid_name+".txt")

    # EXAMPLE
    # [
    # {
    #     'text': 'Hey there',
    #     'start': 7.58,
    #     'duration': 6.13
    # },
    transcript_list = YouTubeTranscriptApi.list_transcripts(url_id)
    for transcript in transcript_list:

        transcript_list = transcript.translate('es').fetch()
        transcript_list_en = transcript.translate('en').fetch()
        transcript_list_ja = transcript.translate('ja').fetch()
        transcript_list_it = transcript.translate('it').fetch()

        # version incompleta sin el idioma ingles
        count = 0
        with open(hard_folder,"w",encoding='utf-8') as txt_file:
            for (line_i,line_k,line_l) in zip(transcript_list,transcript_list_ja,transcript_list_it):
                if(count%20==0): txt_file.write(f"\nstart: {line_i['start']},duraction: {line_i['duration']}\n")
                if(count%2==0):  txt_file.write(f"{line_i['text']}")
                if(count%2==1):  txt_file.write(f" {line_i['text']}\n")
                count += 1
                # txt_file.write(line_l['text']+"\n")
                # txt_file.write(line_k['text']+"\n\n")
    if(debug):
        print(Fore.YELLOW,"action_download_captions",Fore.WHITE)
        print("captions_folder: ",captions_folder)
        print("categoria: ",categoria)

#obtine la informacion para luego llamar a action_download_captions
# EXAMPLES:
def aux_download_captions(url:str,categoria:str,download_folder:str):
    
    # DEBUGGIN
    if debug:
        print(Fore.YELLOW,"aux_download_captions",Fore.WHITE)
        print('url:',url)
        print("categoria",categoria)
        print("download_folder: ",download_folder)
    
    create_directories(join(download_folder,categoria))

    try:
        yt = YouTube(url)
        yt.thumbnail_url
        title = yt.title
    except RemoteDisconnected: print(Fore.RED,"Error al crear el objeto youtube",Fore.WHITE)
    except Exception: print_exc()
    
    # VARIABLES
    folder = Folder(title,yt.author,download_folder,categoria)
    new_name = folder.new_name
    fullname_channel = folder.fullname_channel
    # METODO
    action_download_captions(
        name=new_name,
        categoria=categoria,
        url=url,
        captions_folder=CATEGORIA_VIDEOS
    )
~~~
# usr_capture.py
~~~python
### USER PACKAGES
# usar el otro como global
from usr_tk import tk
from usr_tk_obj_list import obj_list,obj_entry
from usr_debug import debug

### OTHER PACKAGES
from tkinter import END,Button
from mss import mss
import json
from os.path import join,exists
from os import mkdir
import cv2
import numpy as np
from colorama import Fore
import pyautogui
# END
# clase con metodos y variables
################################################################################

# captures/linux/0_megasync.png
# terminal version

#estructuras de datos globales
# cambiar al modelo de frame, documentar codigo con imagenes y botones en word

def capture():
    #modificar el directorio de entrada de captura

    tk.withdraw()
    capture_category_str = obj_entry["entry_caption_category"].get()
    entry_name_str = obj_entry["entry_caption_name"].get()

    # bounding_box = {'top': 100, 'left': 0, 'width': 1920, 'height': 1080}
    # sct = mss()
    # sct_img = sct.grab(bounding_box)
    # valores de las variables harcodeadas

    vars = dict()
    with open("./vars.json","r") as file:
        texto = file.read()
        vars = json.loads(texto)
    if capture_category_str in vars: vars[capture_category_str] += 1
    else: vars[capture_category_str] = 0
    with open("vars.json","w") as file: file.write(json.dumps(vars))

    if debug:
        print(Fore.YELLOW,"capture, hace captura de pantalla",Fore.WHITE)
        print("capture_catgory_str: ",capture_category_str)

    if not exists(join("captures",capture_category_str)): 
        mkdir(join("captures",capture_category_str))
    
    # cv2.imwrite(join('%s'%capture_category_str,"%d_%s.png"%(vars[capture_category_str],entry_name_str)),np.array(sct_img))
    ############ LINUX
    myScreenshot = pyautogui.screenshot()
    myScreenshot.save(join('captures','%s'%capture_category_str,"%d_%s.png"%(vars[capture_category_str],entry_name_str)))
    ############ END LINUX
    # obj_entry["entry_caption_category"].delete(0,END)
    # obj_entry["entry_caption_name"].delete(0,END)
    tk.deiconify()
    # print(Fore.YELLOW,"capture", Fore.WHITE)

def clear_caption_name():
    obj_entry["entry_caption_name"].delete(0,END)



# obj_entry = dict()
for (i,list_tmp) in enumerate(obj_list):
    for (j,elem) in enumerate(list_tmp):
        if elem["type"] == "button" and elem["command"]=="capture":
            Button(tk,text=elem["text"],command=capture).grid(row=i,column=j)
        if elem["type"] == "button" and elem["command"]=="clear_caption_name":
            Button(tk,text=elem["text"],command=clear_caption_name).grid(row=i,column=j)
~~~
# usr_debug.py
~~~python
debug = True
~~~
# usr_directories.py
~~~python
# directorios para cada una de las funciones de la interface
from os.path import join,expanduser,exists
from os import mkdir

HOME = expanduser("~")
# IMG = join(HOME, "Desktop","notas","imagenes_videos") #showoptions, openwindow, listdir
# directorio actual de descarga
IMG = "."
# download folder, variables globales, no paso por argumentos
#comentarios de todas las referencias a este direcotirio
NOTAS = "../.."
PATH = join(HOME,"Documents","MEGA89","Music","00_descargas")
CATEGORIA_VIDEOS = "categoria_videos"

def create_directories(*folders)-> None: #crea directorios en general
    for folder in folders:
        if not exists(folder): mkdir(folder) #creando directorio de categoria


# No se crea el directorio de categoria en el directorio de capturas
# Mostrar informacion de funciones y pasos de cada cosa
~~~
# usr_download_video.py
~~~python
from pytube import YouTube, Playlist
from fun_download_youtube.usr_folder import Folder
from usr_captions import action_download_captions
from usr_directories import CATEGORIA_VIDEOS
from fun_download_youtube.fun_download import aux_download_name
from fun_download_youtube.usr_convert_to_image import convert_to_image
from os.path import join
from colorama import Fore
from http.client import RemoteDisconnected
from urllib.error import URLError
from traceback import print_exc
from usr_directories import create_directories


debug = True

#download video with captions
# imprimir el cÃ³digo de algun ejemplo de entrada
# EXAMPLE:
# yt = (obj)
# categoria01 = mates
def download_video(yt:YouTube,url:str,download_folder:str,title:str,categoria01:str,number:int=0) -> bool:
    
    # variables de modificacion para diferente guardado de lo que necesito
    # title if a valid title (?)
    # imprimir toda la informacion con if debug, junto con las funciones y paquetes importados
    # objeto con los atributos, pasarle los atributos y obtenerlos una linea abajo
    # objeto de tipo global

    # VARIABLES
    folder = Folder(title,yt.author,download_folder,categoria01)

    new_name = folder.new_name
    fullname_channel = folder.fullname_channel
    create_directories(folder.absolute_name)

    # METODO
    # documentacion de porque los videos se guardan de esa manera
    # error por si no existen los captions
    # action_download_captions(
    #     name=new_name,
    #     categoria=folder.categoria,
    #     url=url,
    #     captions_folder="."
    # )

    # METODO
    origin_name = aux_download_name(
        yt,
        folder.absolute_name
    )

    if(origin_name=="continua"): origin_name = title
    video_location = join(fullname_channel,origin_name)

    # METODO
    # convert_to_image(
    #     video_location=video_location,      
    #     video_destination=join(CATEGORIA_VIDEOS,categoria01),
    #     video_name=new_name,
    #     number=number
    # )

    # DEBUGGIN
    if debug:
        print(Fore.YELLOW,"download_video",Fore.WHITE)
        print(f'video_location: {video_location}')
        print("video_destination",fullname_channel)
        print("new_name: ",new_name)
        print("number: ",number)
        # print("download_folder: ",download_folder)
        # print(f'categoria01: {categoria01}')
        # print("title: ",title)
        # print("remove origin_name: ",video_location)

    # PENDIENTE: validador de si eslinux windows y que version de escritorio, o un if si no es posible
    # remove(video_location)
    # subprocess.run(["caja",video_location])


def aux_download_ytvideo(url:str,categoria:str,download_folder:str):
    try:
        yt = YouTube(url)
        title = yt.title
        if(download_video(yt,url,download_folder,title,categoria)==""): return #RemoteDisconnected
    except RemoteDisconnected: print(Fore.RED,"Error al crear el objeto youtube",Fore.WHITE)
    except Exception: print_exc()
    if debug:
        print(Fore.YELLOW,"aux_download_ytvideo",Fore.WHITE)
        print("url: ",url)


def aux_download_playlist(url:str,categoria:str,download_folder:str):
    plvideos = Playlist(url)
    for number,yt in enumerate(plvideos.videos):
        print("PlaylistVideo:",number+1,len(plvideos.videos)) # llevar la cuenta de los videos descargados
        try:
            index_video=0
            print("Comenzando descarga desde: ",index_video)
            if(number>=index_video):
                if(download_video(yt=yt,download_folder=download_folder,title=yt.title,categoria01=categoria,number=number)==""): return
        except URLError:
            print(Fore.RED,"Url Fail",Fore.WHITE)
            return

~~~
# usr_download_youtube.py
~~~python
# USER IMPORTS
from fun_download_youtube.fun_dirs import create_directories
from fun_download_youtube.fun_chars import valid_chars
from fun_download_youtube.fun_database import save_info_database
from fun_youtube_url_validation import youtube_url_validation
from usr_captions import aux_download_captions,all_channel_captions
from fun_download_youtube.usr_folder import Folder
from usr_tk_obj_list import obj_entry,obj_list
from usr_tk import tk
from usr_songs import aux_one_song,aux_download_songs
from usr_download_video import aux_download_ytvideo,aux_download_playlist
#validador,validacion,validamente
# botones en tkinter para cada cosa
#este se usa para descargar captions
# from fun_url_validator import youtube_url_validation

# OTHER IMPORTS
from tkinter import Button,END
import youtube_dl
import _thread
from os.path import join
from os import remove
from usr_directories import HOME,IMG,PATH,CATEGORIA_VIDEOS
from youtube_transcript_api import YouTubeTranscriptApi
from pytube import YouTube,Playlist
from urllib.error import URLError
from colorama import Fore
from http.client import RemoteDisconnected
import subprocess
from traceback import print_exc
# from youtube.main import EmptyStringError

debug = True

class EmptyStringError(Exception):pass

def cases_download(type:str,url:str,categoria:str,dd:str="")->None:
# variables no globales dentro de un metodo mas global

    adata_folder = join("D:","fotosdevideos")
    captions_folder = join(HOME,"Desktop","notas","imagenes_captions")

    if dd=="adata":  download_folder = adata_folder
    if dd== "img": download_folder = IMG
    # elementos con combinaciones
    if type=='y': aux_download_ytvideo(url,categoria,download_folder)
    if type=='p': aux_download_playlist(url,categoria,download_folder)
    if type=='s': aux_one_song(url,PATH)
    if type=='ps': aux_download_songs(url,PATH)
    if type=='c': aux_download_captions(url,categoria,download_folder)
    if type=='cc': all_channel_captions(url,categoria)

    # DEBUGGIN
    if debug:
        print(Fore.BLUE,"EJECUCION",Fore.WHITE)
        print(Fore.YELLOW,"cases_download",Fore.WHITE)
        print("adata_folder: ",adata_folder)
        print("url: ",url)


def tk_download_youtube():
    type = obj_entry["entry_download_type"].get()
    url = obj_entry["entry_download_url"].get()
    category = obj_entry["entry_download_category"].get().lower()
    folder = obj_entry["entry_download_folder"].get()
    _thread.start_new_thread(cases_download,(type,url,category,folder,))
    # cases_download(type,url,category,folder)

def tk_clear_windows():
    obj_entry["entry_download_url"].delete(0,END)
    obj_entry["entry_download_category"].delete(0,END)

for (i,list_tmp) in enumerate(obj_list):
    for (j,elem) in enumerate(list_tmp):
        if elem["type"] == "button" and elem["command"]=="tk_download_youtube":
            Button(tk,text=elem["text"],command=tk_download_youtube).grid(row=i,column=j)
        if elem["type"] == "button" and elem["command"]=="clear_windows":
            Button(tk,text=elem["text"],command=tk_clear_windows).grid(row=i,column=j)
        
~~~
# usr_image_to_ico.py
~~~python
from PIL import Image
filename = r'logo.png'
img = Image.open(filename)
img.save('logo.ico')

# icon_sizes = [(16,16), (32, 32), (48, 48), (64,64)]
# img.save('logo.ico', sizes=icon_sizes)
~~~
# usr_open_window.py
~~~python
from usr_tk_obj_list import obj_entry,obj_list
from usr_directories import NOTAS
from usr_tk import tk

from tkinter import Button
from os import walk,listdir
from os.path import join
import subprocess


def show_options():
    str_var = obj_entry["str_folder_list"]
    menu_str = str_var.get()
 
    # objetos gloables en una clase a parte
    menu_videos = obj_entry["menu_folder_root"]["menu"]
    str_var02 = obj_entry[8]
    menu02 = obj_entry[9]["menu"]
    # videos_str =

    menu_videos.delete(0, "end")
    for (root,subdir,files) in walk(join(NOTAS),menu_str):
        if not len(files) == 0:
            # comando para aÃ±adir una lista de opciones
            menu02.add_command(label=files[0],command=lambda value=files[0]: str_var02.set(value))



def open_window():
    folder = obj_entry["menu_folder_root"].get()
    for (root,subdir,file) in walk(NOTAS):
        # nombre de los directorios
        if not len(file) == 0:
            print("file",file)
            print("folder",root)
            # subprocess.Popen(r'explorer /select,%s'%file)
            #subprocess con un folder si funciona
            # subprocess.run(["C:\\Windows\\explorer.exe",root])
            subprocess.run(["caja",root])
            return

for (i,list_tmp) in enumerate(obj_list):
    for (j,elem) in enumerate(list_tmp):
        if elem["type"] == "button" and elem["command"]=="open_window":
            Button(tk,text=elem["text"],command=open_window).grid(row=i,column=j)
~~~
# usr_songs.py
~~~python
import youtube_dl
from pytube import Playlist
from os.path import join

def aux_one_song(video_url,path_destination):
    video_info = youtube_dl.YoutubeDL().extract_info(url=video_url,download=False)
    filename = f"{video_info['title']}.mp3"
    FINAL_PATH = join(path_destination,filename)
    options={'format':'bestaudio/best','keepvideo':False,'outtmpl':FINAL_PATH,}
    with youtube_dl.YoutubeDL(options) as ydl: ydl.download([video_info['webpage_url']])
    # print("Download complete... {}".format(filename))

def aux_download_songs(video_url:str,path):
    playlist = Playlist(video_url)
    video_urls = playlist.video_urls
    i=0
    for url in video_urls:
        # uso otro de los metodos
        try: aux_one_song(url,path)
        except Exception as exception: print(exception)
        print("[song] {}/{}".format(i,video_url.__len__))
~~~
# usr_tk.py
~~~python
from tkinter import Tk,PhotoImage

tk = Tk()
tk.title("YOUTUBE DOWNLOADER")
# tk.iconbitmap('logo.ico')
tk.iconphoto(False,PhotoImage(file='play-button.png'))

obj_list = []
obj_entry = dict()
~~~
# usr_tk_obj_list.py
~~~python
#CLASS add_to_interface

# issues del programa en github


from usr_tk import tk,obj_entry,obj_list #importacion modo de arbol

from usr_directories import IMG,NOTAS

import subprocess
from tkinter import Label,Entry,Button,OptionMenu,StringVar,END,Text
from os.path import join
from os import listdir,walk
from colorama import Fore
# from usr_capture import capture
# firma de la funcion y definicion posterior, grafica que aun no tiene los nodos
# hacer globales los objetos pero con valor nulo correr este codigo y llenarlos
# static class python

#historial de ultimos videos vistos

# print more messages in code
# descarga de la miniatura de la imagen del video, video info
# conecciÃ³n de la miniatura con django

# descarga del video de vulkan

# ordenar todo el codigo por acciones de borrado y queryes de codigo

debug = True

def clear_windows():
    obj_entry["entry_download_url"].delete(0,END)
    obj_entry["entry_download_category"].delete(0,END)
    # obj_entry["entry_download_folder"].delete(0,END)
# Mostrar opciones

folder_list = listdir(NOTAS)

obj_list = [
    [  
      {"type":"label","in":"frame","text":"CAPTURE:"},
      {"type":"label","in":"frame","text":"Category:"},
      {"type":"entry","in":"frame","name":"entry_caption_category"},

      {"type":"label","in":"frame","text":"Name:"},
      {"type":"entry","in":"frame","name":"entry_caption_name"},

      {"type":"button","in":"frame","text":"clear","command":"clear_caption_name"},

      {"type":"label","in":"frame","text":"Directory:"},
      {"type":"entry","in":"frame","name":"entry_caption_directory"},

      {"type":"button","in":"frame","text":"capture","command":"capture"},
    ],
    [
      {"type":"label","in":"frame","text":"DOWNLOAD:"},
      {"type":"label","in":"frame","text":"Type:"},

      {"type":"optionmenu","in":"frame","varstr":StringVar(tk),"array":["y","y","p","s","ps","c","cc"],"name_str":"entry_download_type","name_menu":"entry_menu"},
      {"type":"label","in":"frame","text":"Url:"},

      {"type":"entry","in":"frame","name":"entry_download_url"},
      {"type":"label","in":"frame","text":"Category:"},
      {"type":"entry","in":"frame","name":"entry_download_category"},
      {"type":"label","in":"frame","text":"Folder:"},
      {"type":"optionmenu","in":"frame","varstr":StringVar(tk),"array":["img","adata"],"name_str":"entry_download_folder","name_menu":"entry_download_folder_menu"},
      {"type":"button","in":"frame","text":"capture","command":"tk_download_youtube"},
      {"type":"button","in":"frame","text":"clear","command":"clear_windows"},
    ],
    [
        {"type":"label","in":"frame","text":""},
    ],
    [
      {"type":"label","in":"frame","text":"WRITE:"},
      {"type":"label","in":"frame","text":"Category:"},
      {"type":"entry","in":"frame","name":"entry_write_category"},
      {"type":"button","in":"frame","text":"clear","command":"clear_category"},
      {"type":"label","in":"frame","text":"Write:"},
      {"type":"entry","in":"frame","name":"entry_write_file"},
      {"type":"button","in":"frame","text":"write","command":"write"},
    ],
    [ 
      {"type":"label","in":"frame","text":"OPEN:"},
      {"type":"optionmenu","in":"frame","varstr":StringVar(tk),"array":folder_list,"name_str":"str_folder_list","name_menu":"menu_folder_root"},
      {"type":"button","in":"frame","text":"open","command":"show_options"},
      {"type":"optionmenu","in":"frame","varstr":StringVar(tk),"array":["none"],"name_str":"str_folder_list_02","name_menu":"menu_folder_root_02"},
      {"type":"button","in":"frame","text":"open","command":"open_window"},
    ],
    [
        {"type":"label","in":"frame","text":""},
        {"type":"text","in":"frame","name":"show_write"},
        {"type":"button","in":"frame","text":"show","command":"show_content"},

    ],

]


obj_entry = dict()

# modelado de la aplicaciÃ³n
# insertados en el frame tk,decirles ademas en que frame, cambiando tambiÃ©n las StringVar

# ejemplo de accesos alos diccionarios

for (i,list_tmp) in enumerate(obj_list):
    for (j,elem) in enumerate(list_tmp):
        if elem["type"] == "label":
            Label(tk,text=elem["text"]).grid(row=i,column=j)
        if elem["type"] == "entry":
            #obtengo el nombre en esa lista y lo guardo en el diccionario
            obj_entry[elem["name"]] = Entry(tk)
            obj_entry[elem["name"]].grid(row=i,column=j)
        # define the commands of the buttons after in another step
        # how to  know column and row
        # if elem["type"] == "button":
        #     Button(tk,text=elem["text"],command=elem["command"]).grid(row=i,column=j)
        if elem["type"]=="text":
            name_text_obj = elem["name"]
            if debug:
                print(Fore.YELLOW,"obj_entry",Fore.WHITE)
                print("name_text_obj",name_text_obj)
            obj_entry[name_text_obj] = Text(tk, height=10,width=25)
            obj_entry[name_text_obj].grid(row=i,column=j)
        if elem["type"]=="optionmenu":
            var_str = elem["varstr"]
            arr_tmp = elem["array"]
            var_str.set(arr_tmp[0])
            obj_entry[elem["name_str"]] = var_str
            obj_entry[elem["name_menu"]] = OptionMenu( tk,var_str,*arr_tmp)
            obj_entry[elem["name_menu"]].grid(row=i,column=j)

#compia del objeto verdadero o referencia (?)
# obj_entry_02 = obj_entry
~~~
# usr_write.py
~~~python
from usr_tk import tk
from usr_tk_obj_list import obj_list,obj_entry
from usr_directories import NOTAS, create_directories

from os.path import join
from tkinter import Button,END
from colorama import Fore
from usr_debug import debug

# nombre de accion en base de datos

# def show_content():

# category_list: ['arbol']
# category_list_tmp:  ['../../arbol']

# documentacion con colores
# acciones de los metodos
# mejor hacer los scripts con python, con validaciones de si es linux o windows

def write_fun():
    # crear tu propia azucar sintactica en el compilador
    # que se autodocumente
    category = obj_entry["entry_write_category"].get()
    category = category.lower()
    #mostrar el primero de la categoria
    # funcion general de objetos
    category_list = category.split(",")
    write_str = obj_entry["entry_write_file"].get()

    # nombre de funciones como lo que les va a pasar despues
    # falta de la creacion de los archivos
    category_list_tmp = list(map(lambda x: join(NOTAS,x), category_list))
    print("category_list", category_list_tmp)
    create_directories(*category_list_tmp)

    text_area = obj_entry["show_write"]
    text_area.delete('1.0',END)
    # category = obj_entry["entry_write_category"].get()
    # category = category.lower()
    # category_list = category.split(",")

    # paralelismo entre variables
    # es mejor dicccionarios para que no pase esto
    first_elem = category_list[0]
    # category_list_tmp = list(map(lambda x: join(NOTAS,x),category_list))
    # variables como objetos de la interfaz
    first_path = category_list_tmp[0]

    # crear si no existe y appendear
    # crear el archivo si no existe y luego appendear


    with open(join(first_path,f"{first_elem}.txt"),"a+") as file:
        text_area.insert(END,file.read())
    

    for  path,name in zip(category_list_tmp,category_list):
        print("path: ",path)
        print("name: ",name)
        # append crea el archivo, no iterar sobre los 2 elem
        with open(join(path,f"{name}.txt"),"a") as file:
            file.write(f"{write_str}\n")
    

    # obj_entry["entry_write_category"].delete(0,END)
    obj_entry["entry_write_file"].delete(0,END)

    if debug:
        print(Fore.YELLOW,"write_fun",Fore.WHITE)
        print("category_list: ",category_list)
        print("category_list_tmp: ",category_list_tmp)



def clear_category():
    obj_entry["entry_write_category"].delete(0,END)


# obj_entry = dict()
for (i,list_tmp) in enumerate(obj_list):
    for (j,elem) in enumerate(list_tmp):
        if elem["type"] == "button" and elem["command"]=="write":
            Button(tk,text=elem["text"],command=write_fun).grid(row=i,column=j)
        if elem["type"] == "button" and elem["command"]=="clear_category":
            Button(tk,text=elem["text"],command=clear_category).grid(row=i,column=j)
        # if elem["type"] == "button" and elem["command"]=="show_content":
        #     Button(tk,text=elem["text"],command=show_content).grid(row=i,column=j)
        
~~~
# __init__.py
~~~python
~~~
# fun_chars.py
~~~python
from re import sub,Match,match

class EmptyStringError(Exception):pass

def valid_chars(character:str)-> str:
    if(character==""): raise EmptyStringError
    title_tmp = character.encode("ascii","ignore").decode() #que regresa encode (?)
    title_ascii = sub(r'[\:\/\?\.\!\,\[\]\\\|\"\']',"",title_tmp)
    return title_ascii
~~~
# fun_database.py
~~~python
from os.path import join
# Examples that the objects
# save info in archive
def save_info_database(new_name,categoria01,channel,download_folder):
    sql_info = "INSERT INTO video (name,categoria,channel) VALUES ({},{},{});\n".format(new_name,categoria01,channel)
    with open(join(download_folder,"videos.sql"),"a") as file: file.write(sql_info)
~~~
# fun_dirs.py
~~~python
from os import mkdir
from os.path import exists
def create_directories(*folders)-> None: #crea directorios en general
    for folder in folders:
        if not exists(folder): mkdir(folder) #creando directorio de categoria
~~~
# fun_download.py
~~~python
from pytube import YouTube
from colorama import Fore
from urllib.error import URLError
# son errores pero regresan cosas en los casos
# nombre con lo que regresa
# funcion auxiliar estandar con colores
# funcion auxiliar estandar del archivo de configuracion
# metodo que esta dentro de una iteracion
 # UN error que no es tan error
def aux_download_name(yt:YouTube,arg_folder:str) -> str:
    """
    - permitir que en uno de los casos de error el proceso continue, con sus respectivos mensajes
    - en caso de error debe seguir pero ya no con el elemento de esa iteracion
    :return: la cadena con el nombre de la descarga
    """
    try:
        title_download = yt.streams.filter(progressive=True, file_extension='mp4').order_by('resolution').desc().first().download(arg_folder)
    except URLError:
        print(Fore.RED+"Url no encontrada"+Fore.WHITE)
        return "continua"
    except ConnectionAbortedError:
        print(Fore.RED+"Conexion abortada, el video no se descargo"+Fore.WHITE)
        raise
    except ConnectionResetError:
        print(Fore.RED+"Connection Reset Error, puede que el video ya se haya descargado"+Fore.WHITE)
        return "continua"
    return title_download
~~~
# usr_convert_to_image.py
~~~python
from cv2 import VideoCapture,imwrite,destroyAllWindows
from os.path import join

# video_location: /home/windows/Users/cnaranjo/Desktop/notas/script/youtube_windows/categoria_videos/mates/The Mandelbrot Set - Numberphile.mp4
# video_destination: ./mates/Numberphile
# new_name: The Mandelbrot Set - Numberphile
# number: 0
def convert_to_image(video_location:str,video_destination:str,video_name:str,number:int,framerate:int=96)-> None:
    cap = VideoCapture(video_location)
    i,j=0,0
    while(cap.isOpened()):

        ret, frame = cap.read()
        if ret == False: break

        # cada 192 frames, 96, 180+12
        if(i%framerate==0):
            full_name = join(video_destination,str(number)+"_"+video_name+"_"+str(j)+".jpg")
            imwrite(full_name, frame)
            j+=1
        i += 1
    i=0
    cap.release()
    destroyAllWindows()
~~~
# usr_folder.py
~~~python
# from fun_download_youtube.fun_database import save_info_database
from fun_download_youtube.fun_database import save_info_database
from usr_directories import create_directories, CATEGORIA_VIDEOS

from colorama import Fore
from os.path import join
from re import sub

# importar la variable debug
debug = True

class EmptyStringError(Exception):pass

def valid_chars(character:str)-> str:
    if(character==""): raise EmptyStringError
    title_tmp = character.encode("ascii","ignore").decode() #que regresa encode (?)
    title_ascii = sub(r'[\:\/\?\.\!\,\[\]\\\|\"\']',"",title_tmp)
    return title_ascii

class Folder():
    """
    - combinacion, nombre, nombre valido, nombre valido ruta absoluta, categoria y canal
    - creacion de los directorios
    - otras formas de guardar la informacion
    - numero id de cada una de las imagenes
    """
    # directorio de descarga como img
    def __init__(self,title,author,download_folder,categoria01):
        # flujo de las cosas que hace el programa
        # listas de creacion de directorios, o un arbol de modificacion, para saber como guardarlo
        self.new_name = valid_chars(title)
        self.channel = valid_chars(author)
        self.categoria = join(CATEGORIA_VIDEOS,categoria01)# nombre personalizado sin terminacion
        self.absolute_name = join(self.categoria,self.new_name)
        self.fullname_channel = join(download_folder,categoria01,self.channel)# nombre personalizado sin terminacion
        # create_directories(join(CATEGORIA_VIDEOS,self.categoria)) #creacion de los directorios
        create_directories(self.categoria) #creacion de los directorios
        #Ejemplos con los parametros que recibe cada funcion
        save_info_database(self.new_name,categoria01,self.channel,download_folder)
        if debug:
            print(Fore.YELLOW,"Folder",Fore.WHITE)
            print("absolute_name: ",self.absolute_name)
~~~
# __init__.py
~~~python
~~~
