## Adversarial Reprogramming on Speech Command Recognition

<img src="https://github.com/dodohow1011/SpeechAdvReprogram/blob/main/illustration.png" width="500">

### Environment

Tensorflow 2.2 (CUDA=10.0) and Kapre 0.2.0. 

- option 1 (from yml)

```shell
conda env create -f repr-scr.yml
source activate repr-scr
```

- option 2 (from clean python 3.6)

```shell
pip install tensorflow-gpu==2.1.0
pip install kapre==0.2.0
pip install h5py==2.10.0
```

### Dataset

Arabic Speech Commands dataset

- Please download the Arabic Speech Commands dataset [here](https://github.com/ltkbenamer/AR_Speech_Database.git).

```shell
./prepare_ar_data.sh
```

Lithuanian Speech Commands dataset

- Please download the Lithuanian Speech Commands dataset [here](https://github.com/kolesov93/lt_speech_commands).

```shell
./prepare_lt_data.sh
```

Dysarthric Speech Commands dataset

- Please download the Lithuanian Speech Commands dataset [here](https://reurl.cc/a5vAG4).

```shell
./prepare_dm_data.sh
```

### Training

For training and evaluating the three speech command recognition results.

```shell
./run_ar.sh
./run_lt.sh
./run_dm.sh
```
For more details please refer to [AR-SCR](https://github.com/dodohow1011/SpeechAdvReprogram/blob/main/AR-SCR/main.py), [LT-SCR](https://github.com/dodohow1011/SpeechAdvReprogram/blob/main/LT-SCR/main.py) and [DM-SCR](https://github.com/dodohow1011/SpeechAdvReprogram/blob/main/DM-SCR/main.py)

(**Optional**) Note that in our default setting we use the random mapping strategy. To enable the similarity mapping,
please modify the code at [utils.py](https://github.com/dodohow1011/SpeechAdvReprogram/blob/main/utils.py#L19) as followed:
```python
def multi_mapping(prob, source_num, mapping_num, target_num):
    
    similarity_mapping = True
```
And choose [lable_map](https://github.com/dodohow1011/SpeechAdvReprogram/blob/27db34e75f048903f296981d5c6e9a2d7a32f742/utils.py#L31-L33) according to your task. You can also see and check mapping results for each task by running the following command:
```sh
python AR-SCR/source_target_pairing.py
python LT-SCR/source_target_pairing.py
python DM-SCR/source_target_pairing.py
```


#### Please consider to cite this work if you use the provided code or find the idea related to your research. Thank you!

- A Study of Low-Resource Speech Commands Recognition Based on Adversarial Reprogramming [Paper](https://arxiv.org/pdf/2110.03894.pdf)

```bib

@article{yen2023neural,
  title={Neural model reprogramming with similarity based mapping for low-resource spoken command classification},
  author={Yen, Hao and Ku, Pin-Jui and Yang, Chao-Han Huck and Hu, Hu and Siniscalchi, Sabato Marco and Chen, Pin-Yu and Tsao, Yu},
  journal={Proc. of Interspeech},
  year={2023}
}

```

### Related References


- Voice2Series: Reprogramming Acoustic Models for Time Series Classification [Paper](https://arxiv.org/pdf/2106.09296.pdf)

```bib

@InProceedings{pmlr-v139-yang21j,
  title = 	 {Voice2Series: Reprogramming Acoustic Models for Time Series Classification},
  author =       {Yang, Chao-Han Huck and Tsai, Yun-Yun and Chen, Pin-Yu},
  booktitle = 	 {Proceedings of the 38th International Conference on Machine Learning},
  pages = 	 {11808--11819},
  year = 	 {2021},
  volume = 	 {139},
  series = 	 {Proceedings of Machine Learning Research},
  month = 	 {18--24 Jul},
  publisher =    {PMLR},
}

```

- Database for Arabic Speech Commands Recognition [Paper](https://www.researchgate.net/publication/346962582_Database_for_Arabic_Speech_Commands_Recognition)

- Voice Activation for Low-Resource Languages [Paper](https://www.mdpi.com/2076-3417/11/14/6298)

- Unsupervised Pre-Training for Voice Activation [Paper](https://www.mdpi.com/2076-3417/10/23/8643)

- A Speech Command Control-Based Recognition System for Dysarthric Patients Based on Deep Learning Technology [Paper](https://www.mdpi.com/2076-3417/11/6/2477)
