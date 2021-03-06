# AULIOS - Challenge 
## Explanation
### Task 
Your task is to create an music visualization program, that translates audio into a 1-dimensional visualization. 
Ideally you would create a visualization that comes off as creative & appealing.
Feel free to use all the audio data available to you in whatever way you would find suitable

We have provided you with a basic setup, that does the following:
1. It can read in an audio file & do some basic analysis on the audio data (a Fast Fourier Transform(FFT)) -> AudioPlayer.py.
2. A callback function that is called in realtime, 60 times a second, that can use the audio data to send out pixel data to the simulator -> app.py.
3. A simulator, consisting of 100 pixels arranged in a 1-dimensional array, for which you can control each pixel's red, green & blue value -> simulator.py

Additionally, we have provided you with three test songs in the songs folder, which you can use to test out your visualization program.

### Rules 
- you can use every resource avaible
- you can use any libraries you want
- you can modify everything of the code **except for the simulator.py**
- fork this GitHub repo and invite me **ElbartoLennyy** to the repo latest by 6th of March 24:00
- all commits after this date won't be accepted

## Getting started

```sh
$ pip install -r requirements.txt
```
- install PyAudio for your python envirement
[**for windows:**](https://stackoverflow.com/posts/55630212/edit)

First start the simulation with:
```sh
$ python simulator.py
```

Than start the application with:
```sh
$ python app.py "songs/MEDUSA - Tell It To My Heart.wav"
```

- by default, the simulator should display an entirely red LED strip because it is receiving the data from app.py 
- the sound will be played via the default speaker

## Documentation

### Simulator 
The Simulator represents an RGB Led Strip with a fixed number of LEDs. Configurable in config.py.

It is also a local UDP Server that listens on port 4210 and runs on 127.0.0.1. It receives UDP packets, interpreted as a list of color values for RGB LEDs. In the format of:
```python
 [RED, GREEN, BLUE, RED, GREEN, BLUE, ...].
```
### SendData
SendData is a simple UDP Client that sends UDP packets to the Simulator. It is used to send the color values of the LED strip.

It takes a 2-dimensional array of uint8 values as input. The array is interpreted as a list of RGB LEDs. The first dimension is the LED color, and the second dimension is the LED index. 
For example: 

```python
[[RED,RED,RED...],[GREEN,GREEN...],[BLUE...]]
```

### AudioPlayer
The AudioPlayer plays wav audio files via the default speaker. It takes a callback function as an argument, which receives the raw audio data and the FFT data of the current audio frame. 

### app
The app initializes the AudioPlayer and the SendData. It also starts the audio stream. **There, you can begin implementing your own logic.**