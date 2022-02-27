# AULIOS - Challenge 
## Explanation
### Task 
- you have three different songs in the songs folder 
- your task is to visualize these three songs in a creative & appealing way
- you can do it in realtime, preprocess the song or everything else that comes into your mind

### Rules 
- you can use every resrouce avaible
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
$ python app.py
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