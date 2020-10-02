# tsaLib

This repository contains some files needed for the labs of TraiSignAp lecture.

## cWave.py 

Small library to read/write wav files through the `cWave` class.

### How to create a wav file

```Python
from sys import path
path.append('../tsaLib')
from cWave import cWave

Fs=44100 # sampling rate in [Hz]
f=440 # sine wav at 440[Hz]
duration=2. # length in [s]

t=np.linspace(0,duration,duration*Fs)
x=np.cos(2*np.pi*f*t)

w=cWave()
frame=32767*np.reshape( x, (len(x),1))
print(x.shape)
w.writeWaveFile( 'sound.wav', Fs,frame.astype('int16'))
``` 

### How to read a wave file

```Python

from sys import path
path.append('../tsaLib')
from cWave import cWave

s='sound.wav'

w=cWave()
w.readWaveFile(s,display=True)
fs,x=w.getLeftData();

# normalization -1...+1
xMax=np.max(np.abs(x))
x=x/xMax 
print('Fs={}[Hz], numSamples={}'.format(fs,len(x)))
N=len(x)
print('min(x)=%+.3f  max(x)=%+.3f' %(np.min(x),np.max(x)))
``` 

