---
This project aimed to use yolo v4 to detect the splash of Western Australia's high speed road. 

**Implementation of YOLO V4**  
The implement of yolo v4 comes from Alexeyab's Github:<https://github.com/alexeyab/darknet>, which provides the source code of  as well as darknet for cross OS platform. You need to first compile then run the demo.  

The introduction covers most your demand of the task.
It provides step by step tutorial of:  

* How to compile it

* How
   to run detection with pre-trained weights of image and vedio
* How to train it for custom object detection
  ·How to test the validation  
* How to write your confiuration file
* How to adjust parameters

**Environment**  
Th environment I used is Google Colab, with [tutorial](https://colab.research.google.com/notebooks/basic_features_overview.ipynb).  
After you learned colab, you can apply this projet on it follw this [tutorial](https://colab.research.google.com/drive/12QusaaRj_lUwCGDvQNfICpa7kA7_a2dE#scrollTo=q2Jjv0yRKLPe)  

**Step by step guide**  

1. Firstly, you can access [My Google Drive](https://drive.google.com/drive/folders/1eFZlbQ-vHVgmMp1-RnjOuFyb0xsKUnvp?usp=sharing)[^1]
2. Move the folder 'Yolo' into the same dirctory in your Google Drive for Colab's run.
3. If you don't  do step 3, you need to replace all the path in below's file.
4. Open my [Colab file](https://colab.research.google.com/drive/1Jo0ikwcJ2E37Ea6aI-coVFNVy5XdxY_x?usp=sharing) and run it cell by cell to detect the the splash for a vedio
5. The final Command is for train the model with the splash dataset.
[^1]: Here is almost the same as github only added some config flie to do splash detection

**Files Introduction**  
There are only 3 files need you to write for train the network.  

1. obj.Data   --	which indicates your trainning set and valid
2. obj.cfg    --	which contains the configuration of your custom network
3. obj.names  --	which contains the name of your aimed object. Besids, here are some other files:

And also other files as blow. <u>Those file with link means you can't find it in github since the size  exceed 100M, you can only get it from Google Drive</u>:  

| File name                                                    | Details                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Yolo-obj_final.weights](https://drive.google.com/file/d/1GdylZYxp1SCN35GGap4bbFVZbLwUnEnR/view?usp=sharing) | The weights I trained to detect splash. You can directly apply it to replace the pretrained-weights of Alexey's project to get the detector. |
| [OriginalVedio](https://drive.google.com/file/d/1GWkwaRIv7tUMoQzjxB6-SIkIywp0RLPD/view?usp=sharing) | It provides a original vedio without result                  |
| [ResultVedio](https://drive.google.com/file/d/160hvHmNKbEX6VUjnDCZk3G4InY4O_nJ_/view?usp=sharing) | It provides a vedio with a result of my detection            |
| Train.txt                                                    | The trainning set index of images.                           |
| Valid.txt                                                    | The valid set index of images.                               |
| obj folder                                                   | All the images and labels file.                              |

**Command**  
Here is the command to use the yolo network:

**Train**				   :	darknet detector train <.data> <.cfg> \<PreTrainWeights\> -dont_show  
**Train by mAP**   ： darknet detector train <.data> <.cfg> \<PreTrainWeights\> -map  
**Detect Image**   ： darknet detector test <.data> <.cfg> \<SelfTraiinedWeights\>  
**Detect Vedion**  ： darknet detector demo <.data> <.cfg> \<SelfTrainedWeights\> -dont_show \<InputVedioPath\> -i 0 -out_filename \<OutputVedioPath\>

Note</u>

1. When follow Alexey's guide to detect vedio, do remember the path of your vedio should be **relative path** from `darknet`. Abosolute path may cause error.

---

***File Path***

All the files you need to change the path to run.  
In the case to run on Google Colab, you first need to mount your Google Drive to Colab.  
Then, you will find your Google Drive at "/content/gdrive/My Drive/"  
Then I created a folder named `Yolo` to store Alexey's repository `darknet`.  
Here listed the path of all my files, if you want to use my cfg, make sure your files are in the same location.  

<u>configuration files:</u>

> * cfg:  "/content/gdrive/My Drive/YOLO/darknet/cfg/yolo-obj.cfg"
> * data: "/content/gdrive/My Drive/YOLO/darknet/data/obj.data"
> * Self-trained Weights: "/content/gdrive/My Drive/YOLO/darknet/backup/yolo-obj_final.weights"
> * names:  “/content/gdrive/My Drive/YOLO/darknet/data/obj.names”
> * PreTraind Weights: "/content/gdrive/My Drive/YOLO/darknet/yolo4.conv.137”  

<u>data files:</u>

> | data        | path                                                         |
> | ----------- | ------------------------------------------------------------ |
> | Images      | "/content/gdrive/My Drive/YOLO/darknet/data/obj/\<ImageName\>.jpeg" |
> | Labels      | "/content/gdrive/My Drive/YOLO/darknet/data/obj/\<labels\>.txt" |
> | Train index | "/content/gdrive/My Drive/YOLO/darknet/data/\<train\>.txt”   |
> | Valid index | "/content/gdrive/My Drive/YOLO/darknet/data/\<valid>.txt”    |

<u>Note</u>

1. When use the path in command line, do use `"path"` instead of `path`, because there is a blank of `My Drive` which may lead to error with out `""`
2. When follow Alexey's guide to detect vedio, do remember the path of your vedio should be **relative path** from `darknet`. Abosolute path may cause error.

