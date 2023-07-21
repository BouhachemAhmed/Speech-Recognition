# Speech-Recognition

OK now let’s create our first example, in this example we are going to convert our audio to text , we want to say something using Microphone, and after that it will be automatically converted to text and saved in our working directory.

import speech_recognition as sr
 
 
def main():
 
    r = sr.Recognizer()
 
    with sr.Microphone() as source:
        r.adjust_for_ambient_noise(source)
 
        print("Please say something")
 
        audio = r.listen(source)
 
        print("Recognizing Now .... ")
 
 
        # recognize speech using google
 
        try:
            print("You have said \n" + r.recognize_google(audio))
            print("Audio Recorded Successfully \n ")
 
 
        except Exception as e:
            print("Error :  " + str(e))
 
 
 
 
        # write audio
        with open("recorded.wav", "wb") as f:
            f.write(audio.get_wav_data())
 
 
if __name__ == "__main__":
    main()
 

 

In here we have created the object of our Recognizer and also we are using Microphone as source. 

r = sr.Recognizer()
 

 

also we need to add this line of code, it is used for removing noises if we have in the sound.

r.adjust_for_ambient_noise(source)
 

 

And in here we are recognizing the speech using Google Speech.

 print("You have said \n" + r.recognize_google(audio))
 

 

If you need to record your audio than you can use this code.

 with open("recorded.wav", "wb") as f:
            f.write(audio.get_wav_data())
 

 

 

Run the code say something in the Microphone and this is the result.

Python Speech Recognition Tutorial for Beginners 
Python Speech Recognition Tutorial for Beginners
 

 

 

Opening Website Using Speech Recognition 
OK now let’s create another example, in this time i want to open a website using speech recognition, for example i want to say google.com in my microphone and after that it will open the website automatically for me, so this the code for this example.

import speech_recognition as sr
import webbrowser as web
 
 
 
def main():
 
    path = "path = "C:/Program Files/Google/Chrome/Application/chrome.exe %s"
 
 
    r = sr.Recognizer()
 
    with sr.Microphone() as source:
        r.adjust_for_ambient_noise(source)
 
        print("Please say something ")
 
        audio = r.listen(source)
 
        print("Reconizing Now ... ")
 
 
 
        try:
            dest = r.recognize_google(audio)
            print("You have said : " + dest)
 
            web.get(path).open(dest)
 
        except Exception as e:
            print("Error : " + str(e))
 
 
if __name__ == "__main__":
    main()
 

 

 

First of all you need to specify the path of your browser, as iam using Google Chrome so this is the path for my browser.

path = "C:/Program Files/Google/Chrome/Application/chrome.exe %s"
 

 

also for removing noises we need to add this line of code.

r.adjust_for_ambient_noise(source)
 

 

In here first we recognize the audio and after that we open the website.

dest = r.recognize_google(audio)
print("You have said : " + dest)
 
web.get(path).open(dest)
 

 

 

Run the code and this is the result.

Python Speech Recognition Opening Website 
Python Speech Recognition Opening Website
 

 

 

Convert Recorded Audio To Text
All right guys till now we have learned that how you can convert your audio using microphone in python, now sometimes you need to convert a recorded audio to text, for example we have a recorded audio and we want to convert this audio to text, so this is the complete code for this.

import speech_recognition as sr
 
 
 
 
def main():
    sound = "recorded.wav"
 
    r = sr.Recognizer()
 
 
    with sr.AudioFile(sound) as source:
        r.adjust_for_ambient_noise(source)
 
 
        print("Converting Audio To Text ..... ")
 
 
        audio = r.listen(source)
 
 
 
    try:
        print("Converted Audio Is : \n" + r.recognize_google(audio))
 
 
    except Exception as e:
        print("Error {} : ".format(e) )
 
 
 
if __name__ == "__main__":
    main()
 

 

OK now in this code we have just changed the source, this time we are using not Microphone, but we are using AudioFile.

with sr.AudioFile(sound) as source:
 

 

Now run the code and this the result, make sure that you have already added a recorded audio in your working directory.

Python Speech Recognition Convert Recorded Audio 
Python Speech Recognition Convert Recorded Audio
 

 

 

Converting Text To Speech in Python
OK we have learned that how you can convert audio to text using google speech in Python, now we want to learn how you can convert text to audio, for this we are using another library. there are two ways the you can convert your Text to Audio or Speech, the first way is using Google Text To Speech (gTTS) library and the second way is usin pyttx3 library.

 

 

What is Google Text To Speech (gTTS) ?
gTTS (Google Text-to-Speech) is a Python library and CLI tool to interface with Google Translate’s text-to-speech API. writes spoken mp3 data to a file, a file-like object (bytestring) for further audio manipulation, or stdout.

 

 

gTTs Installation 
You can use pip for the installation.

pip install gTTS
 

 

So now this is the code for our example.

from gtts import gTTS
 
 
tts = gTTS(text="welcome to my website", lang='en')
tts.save("record.mp3")
print("Text Converted Successfully ")
 

This code convert our text to audio and after that save in our working directory.

 

In the second way we are using pyttsx3 library.

 

 

What is pyttsx3 Library ?
pyttsx3 is a text-to-speech conversion library in Python. Unlike alternative libraries, it works offline, and is compatible with both Python 2 and 3. 

 

pyttsx3 Installation
You can use pip for the installation 

pip install pyttsx3
If you have received errors such as No module named win32com.client, No module named win32, or No module named win32api, you will need to additionally install pypiwin32.

 

 

This is the complete code.

import pyttsx3
 
 
engine = pyttsx3.init()
 
engine.say("welcome to geekscoders website ")
engine.setProperty('rate', 120)
engine.setProperty('volume', 0.9)
engine.runAndWait()
 

 

Run the code and you will see your text converted to audio.
