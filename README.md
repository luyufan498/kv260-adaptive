# xilinx adaptive challenge
## introduction




## demo to show final resualt

<a href="https://www.youtube.com/embed/LHnQx57lm5s" title="YouTube video player"><img src="{image-url}" alt="Alternate Text" /></a>

<iframe width="560" height="315" src="https://www.youtube.com/embed/LHnQx57lm5s" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>









### Model used in our demo

There is one branch for scenario control and two branches for corresponding AI inference.

In our demo, we integrated 5 different types of AI models: 

1) control branch
    segmentation ( s1,s2 ),  
    roadline (model zoo &  self made)

2) people branch
    refinedet  (model zoo & offically supported)
    personID   (from REID)
    openpose  (model zoo & self made)

3) car/traffic branch
    yolo voc2 ()(model zoo & offically supported)
    carID (5 different sizes) (self made & offically supported)  


### pipeline generated in our demo


The control branch is used to provide necessary information for scenario (car or people) detection and control.
    segmentation*
    roadline

The prople branch provides two kinds of mode for people scenario:
    refinedet -> crop -> id* -> tracking
    refinedet -> crop -> openopose
    refinedet (no tracking)

The car branch provides two kinds of mode for car  scenario:
    yolo_v2(adas)* -> crop -> carid* -> tracking
    yolo_v2(adas)* (no tracking)

The test branch:
    yolo_v2(adas)* -> ofa
### functionality switch - adaptivity in functionality

//--------------------------------------------///

1. branch for car : carid
2. branch for people : openpose (with draw and modified crop pulgin) / REID
3. branch for control: segmeation (with draw) and roadline (with draw)

## 4K or 1080P








### hardware switch
1. size of the DPU
    B3136
    B4096
2. frequence of the DPU
    100  200
    275  550


### model size swith
1. carid: 5 different size
2. segmentation: 2 different size

### inference control
1. inference interval
2. enable and disable
3. isbuff

### chart pulgin
1. draw/fill line
6. sample rate
7. refresh rate

2. fps
3. power/temp
4. file
5. DPU time





## code and guide
1. github code: VVAS 
    - build environmemnt
    - compile

2. JSON control
    - ffc 
    - DPU 
        - new model
            - seg
            - road
        - interval
        - enable
        - buff
    - chart 
        - fps
        - power
        - file
        - ffc
        - txt
    - crop
        - w & h
    - post seg
        - txt
        - overlay
    - reid / carid

3. gst
    - inference meta mixed

4. hardware generated

5. preparing model
    - seg: two
    - carid: 5
    - roadline
    - openpose

6. FFC & MMSHARE & FILE



