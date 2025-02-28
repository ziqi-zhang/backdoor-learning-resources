

## Table of Contents
- [Image and Video Classification](#image-and-video-classification) 

  - [Backdoor Defense](#backdoor-defense)
    - [Model Reconstruction based Empirical Defense](#model-reconstruction-based-empirical-defense)
    - [Trigger Synthesis based Empirical Defense](#trigger-synthesis-based-empirical-defense)
    - [Sample Filtering based Empirical Defense](#sample-filtering-based-empirical-defense)
    - [Model Diagnosis based Empirical Defense](#model-diagnosis-based-empirical-defense)
    
  - [Poisoning-based Attack](#poisoning-based-attack)
  - [Non-poisoning-based Attack](#non-poisoning-based-attack)
    - [Weights-oriented Attack](#weights-oriented-attack)
    - [Structure-modified Attack](#structure-modified-attack)
- [Attack and Defense Towards Other Paradigms and Tasks](#attack-and-defense-towards-other-paradigms-and-tasks) 
  - [Collaborative Learning](#collaborative-learning)
  - [Transfer Learning](#transfer-learning) 
  - [Malware Detection](#malware-detection)
- [Discussion and Evaluation](#discussion-and-evaluation)
- [Backdoor Attack for Positive Purposes](#backdoor-attack-for-positive-purposes)

**source-agnostic**: triggers map all inputs to the target label, under the assumption that the features for identifying triggers are separated from those for classifying normal images.

**source-specific**

## Image and Video Classification


### Backdoor Defense

#### Model Reconstruction based Empirical Defense
- Adversarial Unlearning of Backdoors via Implicit Hypergradient.
  [[pdf]](https://arxiv.org/pdf/2110.03735.pdf)
  [[code]](https://github.com/YiZeng623/I-BAU_Adversarial_Unlearning_of-Backdoors_via_implicit_Hypergradient)
  - Yi Zeng, Si Chen, Won Park, Z. Morley Mao, Ming Jin, and Ruoxi Jia. *ICLR*, 2022.
  - remain effective in the extreme case where the defender can only access 100 clean samples -- a setting where all the baselines fail to produce acceptable results.
```diff
+ Unlearning
```

- Adversarial Neuron Pruning Purifies Backdoored Deep Models.
  [[pdf]](https://arxiv.org/pdf/2110.14430.pdf)
  [[code]](https://github.com/csdongxian/ANP_backdoor)
  - Dongxian Wu and Yisen Wang. *NeurIPS*, 2021.
  - with only an extremely small amount of clean data (e.g., 1%)
```diff
+ Pruning
```

- Neural Attention Distillation: Erasing Backdoor Triggers from Deep Neural Networks.
  [[pdf]](https://openreview.net/pdf?id=9l0K4OM-oXE)
  [[code]](https://github.com/bboylyg/NAD)
  - Yige Li, Xingjun Ma, Nodens Koren, Lingjuan Lyu, Xixiang Lyu, and Bo Li. *ICLR*, 2021.
  -  a teacher network to guide the finetuning of the backdoored student network on a small clean subset of data such that the intermediate-layer attention of the student network aligns with that of the teacher network
```diff
+ Knowledge distillation on clean data
```


- Bridging Mode Connectivity in Loss Landscapes and Adversarial Robustness.
  [[pdf]](https://arxiv.org/pdf/2005.00060.pdf)
  [[code]](https://github.com/IBM/model-sanitization)
  - Pu Zhao, Pin-Yu Chen, Payel Das, Karthikeyan Natesan Ramamurthy, and Xue Lin. *ICLR*, 2020.
  - similar to transfer learning and fine-tuning
  - needs a small set of bonafide data

- Fine-Pruning: Defending Against Backdooring Attacks on Deep Neural Networks.
  [[pdf]](https://arxiv.org/pdf/1805.12185.pdf)
  [[code]](https://github.com/kangliucn/Fine-pruning-defense)
  - Kang Liu, Brendan Dolan-Gavitt, and Siddharth Garg. *RAID*, 2018.   


- Disabling Backdoor and Identifying Poison Data by using Knowledge Distillation in Backdoor Attacks on Deep Neural Networks.
  [[pdf]](https://dl.acm.org/doi/pdf/10.1145/3411508.3421375)
  - Kota Yoshida, and Takeshi Fujino. *CCS Workshop*, 2020.
  -  it does not require detecting and identifying backdoor models, backdoor neurons, and poison data.
  -  the defender can collect clean images without labels
```diff
+ Knowledge distillation on clean data
```

- Eliminating Backdoor Triggers for Deep Neural Networks Using Attention Relation Graph Distillation.
  [[pdf]](https://arxiv.org/pdf/2204.09975.pdf)
  - Jun Xia, Ting Wang, Jieping Ding, Xian Wei, and Mingsong Chen. arXiv, 2022.

- Adversarial Fine-tuning for Backdoor Defense: Connect Adversarial Examples to Triggered Samples.
  [[pdf]](https://arxiv.org/pdf/2202.06312.pdf)
  - Bingxu Mu, Le Wang, and Zhenxing Niu. arXiv, 2022.
  - For an infected model, we observe that its adversarial examples have similar behaviors as its triggered samples.
  - need clean data to generate adversarial samples


#### Trigger Synthesis based Empirical Defense
- Better Trigger Inversion Optimization in Backdoor Scanning.
  [[pdf]](https://www.cs.purdue.edu/homes/taog/docs/CVPR22_Tao.pdf)
  [[code]](https://github.com/Gwinhen/PixelBackdoor)
  - Guanhong Tao, Guangyu Shen, Yingqi Liu, Shengwei An, Qiuling Xu, Shiqing Ma, Pan Li, and Xiangyu Zhang. *CVPR*, 2022.
 
- AEVA: Black-box Backdoor Detection Using Adversarial Extreme Value Analysis.
  [[pdf]](https://arxiv.org/pdf/2110.14880.pdf)
  [[code]](https://github.com/aeva-backdoor-deteciton/Aeva-Blackbox-Backdoor-Detection)
  - Junfeng Guo, Ang Li, and Cong Liu. *ICLR*, 2022.
  - black-box hard-label backdoor detection problem where the DNN is fully black-box and only its final output label is accessible.

- Trigger Hunting with a Topological Prior for Trojan Detection.
  [[pdf]](https://arxiv.org/pdf/2110.08335.pdf)
  - Xiaoling Hu, Xiao Lin, Michael Cogswell, Yi Yao, Susmit Jha, and Chao Chen. *ICLR*, 2022.
  - target-label-agnostic reverse engineering method to 
  - recovering multiple triggers on a clean image by manipulating the model’s prediction.
  - perform effectively in cases with unknown target labels.

```diff
reverse engineering the trigger
```

- Black-box Detection of Backdoor Attacks with Limited Information and Data.
  [[pdf]](https://arxiv.org/pdf/2103.13127.pdf)
  - Yinpeng Dong, Xiao Yang, Zhijie Deng, Tianyu Pang, Zihao Xiao, Hang Su, and Jun Zhu. *ICCV*, 2021.
  -  blackbox backdoor detection 
  -  assumption: neither the poisoned training data nor the white-box model can be acquired, with only query-access to the target model
  -  needs clean data
  -  demonstrate the applicability of B3D when using synthetic samples (denoted as B3D-SS) in the case that the clean samples for optimization are unavailable.
```diff
- use synthetic samples
```

- Backdoor Scanning for Deep Neural Networks through K-Arm Optimization.
  [[pdf]](https://arxiv.org/pdf/2102.05123.pdf)
  [[code]](https://github.com/PurduePAML/K-ARM_Backdoor_Optimization)
  - Guangyu Shen, Yingqi Liu, Guanhong Tao, Shengwei An, Qiuling Xu, Siyuan Cheng, Shiqing Ma, and Xiangyu Zhang. *ICML*, 2021.
  - prior limitation: the scanning complexity is quadratic to the number of class labels 
  - It usually assumes a small set of benign inputs for all the classes of the model but not any malicious inputs

- Abs: Scanning neural networks for back-doors by artificial brain stimulation.
  [[pdf]](https://dl.acm.org/doi/pdf/10.1145/3319535.3363216)
  - Yingqi Liu, Wen-Chuan Lee, Guanhong Tao, Shiqing Ma, Yousra Aafer, Xiangyu Zhang, *CCS*, 2019
  - Artificial Brain Stimulation (ABS) (Liu et al., 2019) systematically intercepts and changes internal neuron activation values on benign inputs, and then observes if consistent misclassification can be induced. -- Backdoor Scanning for Deep Neural Networks through K-Arm Optimization.



- Neural Cleanse: Identifying and Mitigating Backdoor Attacks in Neural Networks.
  [[pdf]](https://gangw.web.illinois.edu/class/cs598/papers/sp19-poisoning-backdoor.pdf)
  [[code]](https://github.com/bolunwang/backdoor)
  - Bolun Wang, Yuanshun Yao, Shawn Shan, Huiying Li, Bimal Viswanath, Haitao Zheng, Ben Y. Zhao. *IEEE S&P*, 2019.
  - 10% of training data required in Neural Cleanse according to Few-shot Backdoor Defense Using Shapley Estimation [[pdf]](https://arxiv.org/pdf/2112.14889.pdf)
  - Neural Cleanse (NC) (Wang et al., 2019) uses optimization to derive a trigger for each class and observes if there is any trigger that is exceptionally small and hence likely injected instead of naturally occurring feature. -- Backdoor Scanning for Deep Neural Networks through K-Arm Optimization.
  - requires L\*L times of scaning, L is the number of output classes

- Defending Neural Backdoors via Generative Distribution Modeling.
  [[pdf]](https://arxiv.org/pdf/1910.04749.pdf)
  [[code]](https://github.com/superrrpotato/Defending-Neural-Backdoors-via-Generative-Distribution-Modeling)
  - Ximing Qiao, Yukun Yang, and Hai Li. *NeurIPS*, 2019.
  - Use generative models to generate various triggers

- DeepInspect: A Black-box Trojan Detection and Mitigation Framework for Deep Neural Networks.
  [[pdf]](https://www.ijcai.org/proceedings/2019/0647.pdf)
  - Huili Chen, Cheng Fu, Jishen Zhao, Farinaz Koushanfar. *IJCAI*, 2019.
  - data-free backdoor detection, w/o need of training data
  - the defender can leverage the trigger generator for adversarial training and invalidating the inserted backdoor.
  - model inversion to reverse clean training image
  - only detect whether the model has backdoor, no patching
```diff
+ data-free detection, use GAN to generate trigger, no patching
```

- GangSweep: Sweep out Neural Backdoors by GAN
  [[pdf]](https://dl.acm.org/doi/pdf/10.1145/3394171.3413546)
  - *MM*, 2020
  - use GAN to detect and sweep out NN backdoors
  - GAN to generate triggers and artifacts of the target class
  - outlier detection mechanism that can make a clear distinction between the trigger and the ordinary adversarial perturbations
  - correct the labels of the backdoor samples and completely clean out the infected model through finetuning.
  - needs validation data


- Model-Contrastive Learning for Backdoor Defense.
  [[pdf]](https://arxiv.org/pdf/2205.04411)
  - Zhihao Yue, Jun Xia, Zhiwei Ling, Ting Wang, Xian Wei, and Mingsong Chen. arXiv, 2022.

- Backdoor Defense with Machine Unlearning.
  [[pdf]](https://arxiv.org/pdf/2201.09538.pdf)
  - Yang Liu, Mingyuan Fan, Cen Chen, Ximeng Liu, Zhuo Ma, Li Wang, and Jianfeng Ma. arXiv, 2022.
  - trigger reverse: use generative model to generate trigger
  - Use machine unlearning to erase backdoor. Specifically to use gradient ascent to unlearn backdoor, introduces a weighted penalty mechanism to mitigate catastrophic forgetting
  - the proposed approach gets rid of the reliance on the full access to training data for retraining, but still needs some clean data

```diff
+ machine unlearning the poisoning sample, GAN generates trigger, needs some clean data
```

- Few-shot Backdoor Defense Using Shapley Estimation.
  [[pdf]](https://arxiv.org/pdf/2112.14889.pdf)
  - Jiyang Guan, Zhuozhuo Tu, Ran He, and Dacheng Tao. arXiv, 2021.
  - 1 image per class or even free of data
  - use a loss to reconstruct the training image from poisoned model
  - 
```diff
- prune & limited data & data-free
```

- CatchBackdoor: Backdoor Testing by Critical Trojan Neural Path Identification via Differential Fuzzing.
  [[pdf]](https://arxiv.org/pdf/2112.13064.pdf)
  - Haibo Jin, Ruoxi Chen, Jinyin Chen, Yao Cheng, Chong Fu, Ting Wang, Yue Yu, and Zhaoyan Ming. arXiv, 2021.
  - DNN testing & neural path

- Detect and Remove Watermark in Deep Neural Networks via Generative Adversarial Networks.
  [[pdf]](https://arxiv.org/pdf/2106.08104.pdf)
  - Haoqi Wang, Mingfu Xue, Shichang Sun, Yushu Zhang, Jian Wang, and Weiqiang Liu. arXiv, 2021.
  - 6 pages
  - detect and remove watermark in deep neural networks via generative adversarial networks (GAN)
  - 1. use the GAN and few clean images to detect and reverse the watermark in the DNN model. 2. fine-tune the watermarked DNN
  - needs training data

- TAD: Trigger Approximation based Black-box Trojan Detection for AI.
  [[pdf]](https://arxiv.org/pdf/2102.01815.pdf)
  - Xinqiao Zhang, Huili Chen, and Farinaz Koushanfar. arXiv, 2021.
  - 6 pages
  - backdoor detection, no mitigation

- Scalable Backdoor Detection in Neural Networks.
  [[pdf]](https://arxiv.org/pdf/2006.05646.pdf)
  - Haripriya Harikumar, Vuong Le, Santu Rana, Sourangshu Bhattacharya, Sunil Gupta, and Svetha Venkatesh. arXiv, 2020.
  -  computational complexity does not scale with the number of labels 
  -  is based on a measure that is both interpretable and universal across different network and patch types.
  -  backdoor detection, no mitigation

- NNoculation: Broad Spectrum and Targeted Treatment of Backdoored DNNs.
  [[pdf]](https://arxiv.org/pdf/2002.08313.pdf)
  [[code]](https://github.com/akshajkumarv/NNoculation)
  - Akshaj Kumar Veldanda, Kang Liu, Benjamin Tan, Prashanth Krishnamurthy, Farshad Khorrami, Ramesh Karri, Brendan Dolan-Gavitt, and Siddharth Garg. AISec21.
  - two stages. repairs a BadNet both pre-deployment and online in response to backdoored test inputs encountered in the field.


#### Sample Filtering based Empirical Defense
- Rethinking the Backdoor Attacks' Triggers: A Frequency Perspective.
  [[pdf]](https://arxiv.org/pdf/2104.03413.pdf)
  [[code]](https://github.com/YiZeng623/frequency-backdoor)
  - Yi Zeng, Won Park, Z. Morley Mao, and Ruoxi Jia. *ICCV*, 2021.

- Demon in the Variant: Statistical Analysis of DNNs for Robust Backdoor Contamination Detection.
  [[pdf]](https://arxiv.org/pdf/1908.00686.pdf)
  [[code]](https://github.com/TDteach/backdoor)
  - Di Tang, XiaoFeng Wang, Haixu Tang, and Kehuan Zhang. *USENIX Security*, 2021.
```diff
+ security21
```

- SPECTRE: Defending Against Backdoor Attacks Using Robust Statistics.
  [[pdf]](https://arxiv.org/pdf/2104.11315.pdf)
  [[code]](https://github.com/SewoongLab/spectre-defense)
  - Jonathan Hayase, Weihao Kong, Raghav Somani, and Sewoong Oh. *ICML*, 2021.
  -  separate corrupted examples from clean ones.

- Robust Anomaly Detection and Backdoor Attack Detection via Differential Privacy.
  [[pdf]](https://arxiv.org/pdf/1911.07116.pdf)
  [[code]](https://www.dropbox.com/sh/rt8qzii7wr07g6n/AAAbwokv2sfBeE9XAL2pXv_Aa?dl=0)
  - Min Du, Ruoxi Jia, and Dawn Song. *ICLR*, 2020.  
  
- Simple, Attack-Agnostic Defense Against Targeted Training Set Attacks Using Cosine Similarity.
  [[pdf]](http://www.gatsby.ucl.ac.uk/~balaji/udl2021/accepted-papers/UDL2021-paper-029.pdf)
  [[code]](https://github.com/ZaydH/cosin)
  - Zayd Hammoudeh and Daniel Lowd. *ICML Workshop*, 2021.

- Spectral Signatures in Backdoor Attacks.
  [[pdf]](https://arxiv.org/pdf/1811.00636.pdf)
  [[code]](https://github.com/MadryLab/backdoor_data_poisoning)
  - Brandon Tran, Jerry Li, and Aleksander Madry. *NeurIPS*, 2018.  
  - detecting and removing poisoned examples on real image sets
```diff
use SVD to filter triggered inputs
```

- PiDAn: A Coherence Optimization Approach for Backdoor Attack Detection and Mitigation in Deep Neural Networks.
  [[pdf]](https://arxiv.org/pdf/2203.09289.pdf)
  - Yue Wang, Wenqing Li, Esha Sarkar, Muhammad Shafique, Michail Maniatakos, and Saif Eddin Jabari. arXiv, 2022.

- Towards Effective and Robust Neural Trojan Defenses via Input Filtering.
  [[pdf]](https://arxiv.org/pdf/2202.12154.pdf)
  - Kien Do, Haripriya Harikumar, Hung Le, Dung Nguyen, Truyen Tran, Santu Rana, Dang Nguyen, Willy Susilo, and Svetha Venkatesh. arXiv, 2022.
  - New backdoor types: (1) using multiple, input-specific triggers and (2) targeting multiple classes.

- Neural Network Trojans Analysis and Mitigation from the Input Domain.
  [[pdf]](https://arxiv.org/pdf/2202.06382.pdf)
  - Zhenting Wang, Hailun Ding, Juan Zhai, and Shiqing Ma. arXiv, 2022.
  - assumption:  a complete and accurate Trojan corresponds to a hyperplane decision region in the input domain
  - design a novel training method that removes Trojans during training even on poisoned datasets

- NTD: Non-Transferability Enabled Backdoor Detection.
  [[pdf]](https://arxiv.org/pdf/2111.11157.pdf)
  - Yinshan Li, Hua Ma, Zhi Zhang, Yansong Gao, Alsharif Abuadbba, Anmin Fu, Yifeng Zheng, Said F. Al-Sarawi, and Derek Abbott. arXiv, 2021.
  - online input detection, offline preparation on the validation set to select hyper-parameters
  - has a small survey
  - target Security

- A Unified Framework for Task-Driven Data Quality Management.
  [[pdf]](https://arxiv.org/pdf/2106.05484.pdf)
  - Tianhao Wang, Yi Zeng, Ming Jin, and Ruoxi Jia. arXiv, 2021.
  - filter data during training time

- TESDA: Transform Enabled Statistical Detection of Attacks in Deep Neural Networks.
  [[pdf]](https://arxiv.org/pdf/2110.08447.pdf)
  - Chandramouli Amarnath, Aishwarya H. Balwani, Kwondo Ma, and Abhijit Chatterjee. arXiv, 2021.
  - online detection of attacks by exploiting the discrepancies they cause in the distributions of intermediate layer features of DNNs

- Traceback of Data Poisoning Attacks in Neural Networks.
  [[pdf]](https://arxiv.org/pdf/2110.06904.pdf)
  - Shawn Shan, Arjun Nitin Bhagoji, Haitao Zheng, and Ben Y. Zhao. arXiv, 2021.
  - three dirty-label and three clean-label attacks
  - tracing back attack events to the root cause and fix the attack

- Provable Guarantees against Data Poisoning Using Self-Expansion and Compatibility.
  [[pdf]](https://arxiv.org/pdf/2105.03692.pdf)
  - Charles Jin, Melinda Sun, and Martin Rinard. arXiv, 2021.
  - iterative training procedure for removing poisoned data from the training set.
  
- Online Defense of Trojaned Models using Misattributions.
  [[pdf]](https://arxiv.org/pdf/2103.15918.pdf)
  - Panagiota Kiourti, Wenchao Li, Anirban Roy, Karan Sikka, and Susmit Jha. arXiv, 2021.

- Detecting Backdoor in Deep Neural Networks via Intentional Adversarial Perturbations.
  [[pdf]](https://arxiv.org/pdf/2105.14259.pdf)
  - Mingfu Xue, Yinghao Wu, Zhiyu Wu, Jian Wang, Yushu Zhang, and Weiqiang Liu. arXiv, 2021.

- Exposing Backdoors in Robust Machine Learning Models.
  [[pdf]](https://arxiv.org/pdf/2003.00865.pdf)
  - Ezekiel Soremekun, Sakshi Udeshi, and Sudipta Chattopadhyay. arXiv, 2020.

- A Unified Framework for Analyzing and Detecting Malicious Examples of DNN Models.
  [[pdf]](https://arxiv.org/pdf/2006.14871.pdf)
  - Kaidi Jin, Tianwei Zhang, Chao Shen, Yufei Chen, Ming Fan, Chenhao Lin, and Ting Liu. arXiv, 2020.

- HaS-Nets: A Heal and Select Mechanism to Defend DNNs Against Backdoor Attacks for Data Collection Scenarios.
  [[pdf]](https://arxiv.org/pdf/2012.07474.pdf)
  - Hassan Ali, Surya Nepal, Salil S. Kanhere, and Sanjay Jha. arXiv, 2020.

- Poison as a Cure: Detecting & Neutralizing Variable-Sized Backdoor Attacks in Deep Neural Networks.
  [[pdf]](https://arxiv.org/pdf/1911.08040.pdf)
  - Alvin Chan, and Yew-Soon Ong. arXiv, 2019.  
  
  


#### Model Diagnosis based Empirical Defense - detect whether a model is backdoored

<details>
<summary>Backdoor detection</summary>

#### Model Diagnosis based Empirical Defense
- Complex Backdoor Detection by Symmetric Feature Differencing.
  [[pdf]](https://www.cs.purdue.edu/homes/taog/docs/CVPR22_Liu.pdf)
  [[code]](https://github.com/PurduePAML/Exray)
  - Yingqi Liu, Guangyu Shen, Guanhong Tao, Zhenting Wang, Shiqing Ma, and Xiangyu Zhang. *CVPR*, 2022.

- Post-Training Detection of Backdoor Attacks for Two-Class and Multi-Attack Scenarios.
  [[pdf]](https://arxiv.org/pdf/2201.08474.pdf)
  [[code]](https://github.com/zhenxianglance/2ClassBADetection)
  - Zhen Xiang, David J. Miller, and George Kesidis. *ICLR*, 2022.
  - Detecting whether a classifier is backdoor attacked 
  - These scenarios are first studied in the current paper, under the practical constraints that (1) the defender neither has access to the classifier’s training set nor (2) to supervision from clean reference classifiers trained for the same domain.

- Detecting AI Trojans Using Meta Neural Analysis.
  [[pdf]](https://arxiv.org/pdf/1910.03137.pdf)
  - Xiaojun Xu, Qi Wang, Huichen Li, Nikita Borisov, Carl A. Gunter, and Bo Li. *IEEE S&P*, 2021.
  - prior work impractical assumption: (1) ''all-to-one'' attack is easy to detect, (2) white-box access to the model, (3) clean-data and clean-labell backdoor attack is difficult to detect
  - black-box access to the model, no need training data, need clean data
  - experiments cover CV, NLP, speech, tabular
  - including a brief survey

```diff
+ SP21
```

- Topological Detection of Trojaned Neural Networks.
  [[pdf]](https://arxiv.org/pdf/2106.06469.pdf)
  - Songzhu Zheng, Yikai Zhang, Hubert Wagner, Mayank Goswami, and Chao Chen. *NeurIPS*, 2021.
  - there exists significant structural difference between clean and Trojaned networks.
  - white-box detection

- Black-box Detection of Backdoor Attacks with Limited Information and Data.
  [[pdf]](https://arxiv.org/pdf/2103.13127.pdf)
  - Yinpeng Dong, Xiao Yang, Zhijie Deng, Tianyu Pang, Zihao Xiao, Hang Su, and Jun Zhu. *ICCV*, 2021.
  - including a brief survey
  - need clean data to reverse-engineer the trigger 

- Universal Litmus Patterns: Revealing Backdoor Attacks in CNNs.
  [[pdf]](https://arxiv.org/pdf/1906.10842.pdf)
  [[code]](https://umbcvision.github.io/Universal-Litmus-Patterns/)
  - Soheil Kolouri, Aniruddha Saha, Hamed Pirsiavash, and Heiko Hoffmann. *CVPR*, 2020.
  - detect if the model has backdoor 
  - do not need: 1) access to the training data or 2) running tests on the clean data

- One-Pixel Signature: Characterizing CNN Models for Backdoor Detection.
  [[pdf]](https://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123720324.pdf)
  - Shanjiaoyang Huang, Weiqi Peng, Zhiwei Jia, and Zhuowen Tu. *ECCV*, 2020.
  - detect if the black-box model has backdoor 

  
- Practical Detection of Trojan Neural Networks: Data-Limited and Data-Free Cases.
  [[pdf]](https://arxiv.org/pdf/2007.15802.pdf)
  [[code]](https://github.com/wangren09/TrojanNetDetector)
  - Ren Wang, Gaoyuan Zhang, Sijia Liu, Pin-Yu Chen, Jinjun Xiong, and Meng Wang. *ECCV*, 2020.
  - white-box backdoor model detection
  - leverage the internal response of hidden neurons

- Baseline Pruning-Based Approach to Trojan Detection in Neural Networks.
  [[pdf]](https://aisecure-workshop.github.io/aml-iclr2021/papers/17.pdf)
  - Peter Bajcsy and Michael Majurski. *ICLR Workshop*, 2021.
  - classifies each NN model as clean or poisoned by learning a mapping between accuracy measurements and reference clean or poisoned NN model labels

- Universal Post-Training Backdoor Detection.
  [[pdf]](https://arxiv.org/pdf/2205.06900.pdf)
  - Hang Wang, Zhen Xiang, David J. Miller, and George Kesidis. arXiv, 2022.

- Trojan Signatures in DNN Weights.
  [[pdf]](https://arxiv.org/pdf/2109.02836.pdf)
  - Greg Fields, Mohammad Samragh, Mojan Javaheripi, Farinaz Koushanfar, and Tara Javidi. arXiv, 2021.
  - no need training/test data, no assumption of the nature of the trigger
  - analyze the final linear weights

- EX-RAY: Distinguishing Injected Backdoor from Natural Features in Neural Networks by Examining Differential Feature Symmetry.
  [[pdf]](https://arxiv.org/pdf/2103.08820.pdf)
  - Yingqi Liu, Guangyu Shen, Guanhong Tao, Zhenting Wang, Shiqing Ma, and Xiangyu Zhang. arXiv, 2021.
  - develop a novel symmetric feature differencing method that identifies a smallest set of features separating two classes

- TOP: Backdoor Detection in Neural Networks via Transferability of Perturbation.
  [[pdf]](https://arxiv.org/pdf/2103.10274.pdf)
  - Todd Huster and Emmanuel Ekwedike. arXiv, 2021.
  - w/o training data nor triger pattern
  - adversarial perturbations transfer from image to image more readily in poisoned models than in clean models

- Detecting Trojaned DNNs Using Counterfactual Attributions.
  [[pdf]](https://arxiv.org/pdf/2012.02275.pdf)
  - code https://github.com/SRI-CSL/Trinity-TrojAI
  - Karan Sikka, Indranil Sur, Susmit Jha, Anirban Roy, and Ajay Divakaran. arXiv, 2021.
  - the trigger behavior depends on a few ghost neurons that activate on trigger pattern and exhibit abnormally higher relative attribution for wrong decisions when activated

- Adversarial examples are useful too!
  [[pdf]](https://arxiv.org/pdf/2005.06107.pdf)
  [[code]](https://github.com/aliborji/Backdoor_defense)
  - XBorji A. arXiv, 2020.
  - tell whether a model has been subject to a backdoor attack.

- Cassandra: Detecting Trojaned Networks from Adversarial Perturbations.
  [[pdf]](https://arxiv.org/pdf/2007.14433.pdf)
  - Xiaoyu Zhang, Ajmal Mian, Rohit Gupta, Nazanin Rahnavard, and Mubarak Shah. arXiv, 2020.
  - verify if a pre-trained model is Trojaned or benign
  
- Odyssey: Creation, Analysis and Detection of Trojan Models.
  [[pdf]](https://arxiv.org/pdf/2007.08142.pdf)
  [[dataset]](https://lcwn-lab.github.io/Odessey/)
  - Marzieh Edraki, Nazmul Karim, Nazanin Rahnavard, Ajmal Mian, and Mubarak Shah. arXiv, 2020.

- Noise-response Analysis for Rapid Detection of Backdoors in Deep Neural Networks.
  [[pdf]](https://arxiv.org/pdf/2008.00123.pdf)
  - N. Benjamin Erichson, Dane Taylor, Qixuan Wu, and Michael W. Mahoney. arXiv, 2020.

- NeuronInspect: Detecting Backdoors in Neural Networks via Output Explanations.
  [[pdf]](https://arxiv.org/pdf/1911.07399.pdf)
  - Xijie Huang, Moustafa Alzantot, and Mani Srivastava. arXiv, 2019.

</details>
  
### Poisoning-based Attack

<details>
<summary>Poison attack</summary>

#### 2022

- Trojan Horse Training for Breaking Defenses against Backdoor Attacks in Deep Learning.
  [[pdf]](https://arxiv.org/pdf/2203.15506.pdf)
  - Arezoo Rajabi, Bhaskar Ramasubramanian, and Radha Poovendran. arXiv, 2022.

- Label-Smoothed Backdoor Attack.
  [[pdf]](https://arxiv.org/pdf/2202.11203.pdf)
  - Minlong Peng, Zidi Xiong, Mingming Sun, and Ping Li. arXiv, 2022.

- Imperceptible and Multi-channel Backdoor Attack against Deep Neural Networks.
  [[pdf]](https://arxiv.org/pdf/2201.13164.pdf)
  - Mingfu Xue, Shifeng Ni, Yinghao Wu, Yushu Zhang, Jian Wang, and Weiqiang Liu. arXiv, 2022.

- Compression-Resistant Backdoor Attack against Deep Neural Networks.
  [[pdf]](https://arxiv.org/pdf/2201.00672.pdf)
  - Mingfu Xue, Xin Wang, Shichang Sun, Yushu Zhang, Jian Wang, and Weiqiang Liu. arXiv, 2022.


#### 2021 
- Invisible Backdoor Attack with Sample-Specific Triggers.
  [[pdf]](https://arxiv.org/pdf/2012.03816.pdf)
  [[code]](https://github.com/yuezunli/ISSBA)
  - Yuezun Li, Yiming Li, Baoyuan Wu, Longkang Li, Ran He, and Siwei Lyu. *ICCV*, 2021.

- Manipulating SGD with Data Ordering Attacks.
  [[pdf]](https://arxiv.org/pdf/2104.09667.pdf)
  - Ilia Shumailov, Zakhar Shumaylov, Dmitry Kazhdan, Yiren Zhao, Nicolas Papernot, Murat A. Erdogdu, and Ross Anderson. *NeurIPS*, 2021.

- Backdoor Attack with Imperceptible Input and Latent Modification.
  [[pdf]](https://proceedings.neurips.cc/paper/2021/file/9d99197e2ebf03fc388d09f1e94af89b-Paper.pdf)
  - Khoa Doan, Yingjie Lao, and Ping Li. *NeurIPS*, 2021.

- LIRA: Learnable, Imperceptible and Robust Backdoor Attacks.
  [[pdf]](https://openaccess.thecvf.com/content/ICCV2021/papers/Doan_LIRA_Learnable_Imperceptible_and_Robust_Backdoor_Attacks_ICCV_2021_paper.pdf)
  - Khoa Doan, Yingjie Lao, Weijie Zhao, and Ping Li. *ICCV*, 2021.

- Blind Backdoors in Deep Learning Models. 
  [[pdf]](https://arxiv.org/pdf/2005.03823.pdf)
  [[code]](https://github.com/ebagdasa/backdoors101)
  - Eugene Bagdasaryan, and Vitaly Shmatikov. *USENIX Security*, 2021.
  - New kind of backdoor attack

- Deep Feature Space Trojan Attack of Neural Networks by Controlled Detoxification.
  [[pdf]](https://arxiv.org/pdf/2012.11212.pdf)
  [[code]](https://github.com/Megum1/DFST)
  - Siyuan Cheng, Yingqi Liu, Shiqing Ma, and Xiangyu Zhang. *AAAI*, 2021.

- WaNet - Imperceptible Warping-based Backdoor Attack.
  [[pdf]](https://openreview.net/pdf?id=eEn8KTtJOx)
  [[code]](https://github.com/VinAIResearch/Warping-based_Backdoor_Attack-release)
  - Tuan Anh Nguyen, and Anh Tuan Tran. *ICLR*, 2021.

- AdvDoor: Adversarial Backdoor Attack of Deep Learning System.
  [[pdf]](http://www.wingtecher.com/themes/WingTecherResearch/assets/papers/issta21_learning.pdf)
  [[code]](https://github.com/AdvDoor/AdvDoor)
  - Quan Zhang, Yifeng Ding, Yongqiang Tian, Jianmin Guo, Min Yuan, and Yu Jiang. *ISSTA*, 2021.

- DBIA: Data-free Backdoor Injection Attack against Transformer Networks.
  [[pdf]](https://arxiv.org/pdf/2111.11870.pdf)
  [[code]](https://anonymous.4open.science/r/DBIA-825D)
  - Peizhuo Lv, Hualong Ma, Jiachen Zhou, Ruigang Liang, Kai Chen, Shengzhi Zhang, and Yunfei Yang. arXiv, 2021.

- A Statistical Difference Reduction Method for Escaping Backdoor Detection.
  [[pdf]](https://arxiv.org/pdf/2111.05077.pdf)
  - Pengfei Xia, Hongjing Niu, Ziqiang Li, and Bin Li. arXiv, 2021.

- Backdoor Attack through Frequency Domain.
  [[pdf]](https://arxiv.org/pdf/2111.10991.pdf)
  - Tong Wang, Yuan Yao, Feng Xu, Shengwei An, and Ting Wang. arXiv, 2021.

- Check Your Other Door! Establishing Backdoor Attacks in the Frequency Domain.
  [[pdf]](https://arxiv.org/pdf/2109.05507.pdf)
  - Hasan Abed Al Kader Hammoud and Bernard Ghanem. arXiv, 2021.

- Poison Ink: Robust and Invisible Backdoor Attack.
  [[pdf]](https://arxiv.org/pdf/2108.02488.pdf)
  - Jie zhang, Dongdong Chen, Jing Liao, Qidong Huang, Gang Hua, Weiming Zhang, and Nenghai Yu. arXiv, 2021.

- Sleeper Agent: Scalable Hidden Trigger Backdoors for Neural Networks Trained from Scratch.
  [[pdf]](https://arxiv.org/pdf/2106.08970.pdf)
  [[code]](https://github.com/hsouri/Sleeper-Agent)
  - Hossein Souri, Micah Goldblum, Liam Fowl, Rama Chellappa, and Tom Goldstein. arXiv, 2021.
 
- RABA: A Robust Avatar Backdoor Attack on Deep Neural Network.
  [[pdf]](https://arxiv.org/pdf/2104.01026.pdf)
  - Ying He, Zhili Shen, Chang Xia, Jingyu Hua, Wei Tong, and Sheng Zhong. arXiv, 2021.


#### 2020

- Composite Backdoor Attack for Deep Neural Network by Mixing Existing Benign Features.
  [[pdf]](https://dl.acm.org/doi/pdf/10.1145/3372297.3423362)
  - Junyu Lin, Lei Xu, Yingqi Liu, Xiangyu Zhang. *CCS*, 2020.

- Input-Aware Dynamic Backdoor Attack. 
  [[pdf]](https://arxiv.org/pdf/2010.08138.pdf)
  [[code]](https://github.com/VinAIResearch/input-aware-backdoor-attack-release)
  - Anh Nguyen, and Anh Tran. *NeurIPS 2020*.


- Bypassing Backdoor Detection Algorithms in Deep Learning.
  [[pdf]](https://arxiv.org/pdf/1905.13409.pdf)
  - Te Juin Lester Tan, and Reza Shokri. *EuroS&P*, 2020.

#### 2019

- Label-Consistent Backdoor Attacks.
  [[pdf]](https://arxiv.org/pdf/1912.02771.pdf)
  [[code]](https://github.com/MadryLab/label-consistent-backdoor-code)
  - Alexander Turner, Dimitris Tsipras, and Aleksander Madry. arXiv, 2019.

#### 2018
- Trojaning Attack on Neural Networks.
  [[pdf]](https://docs.lib.purdue.edu/cgi/viewcontent.cgi?referer=&httpsredir=1&article=2782&context=cstech)
  [[code]](https://github.com/PurduePAML/TrojanNN)
  - Yingqi Liu, Shiqing Ma, Yousra Aafer, Wen-Chuan Lee, and Juan Zhai. *NDSS*, 2018.
 
#### 2017
- BadNets: Identifying Vulnerabilities in the Machine Learning Model Supply Chain.
  [[pdf]](https://arxiv.org/pdf/1708.06733.pdf)
  [[journal]](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8685687)
  - Tianyu Gu, Brendan Dolan-Gavitt, and Siddharth Garg. arXiv, 2017 (*IEEE Access*, 2019).

- Targeted Backdoor Attacks on Deep Learning Systems Using Data Poisoning.
  [[pdf]](https://arxiv.org/pdf/1712.05526.pdf)
  [[code]](https://github.com/GeorgePisl/backdoor-attacks-based-on-deep-learning)
  - Xinyun Chen, Chang Liu, Bo Li, Kimberly Lu, and Dawn Song. arXiv, 2017.  

</details>

### Non-poisoning-based Attack 

<details>
<summary>Non-poison attack</summary>

#### Weights-oriented Attack
- ProFlip: Targeted Trojan Attack with Progressive Bit Flips. 
  [[pdf]](https://openaccess.thecvf.com/content/ICCV2021/papers/Chen_ProFlip_Targeted_Trojan_Attack_With_Progressive_Bit_Flips_ICCV_2021_paper.pdf)
  - Huili Chen, Cheng Fu, Jishen Zhao, and Farinaz Koushanfar. *ICCV*, 2021.

- TBT: Targeted Neural Network Attack with Bit Trojan.
  [[pdf]](https://arxiv.org/abs/1909.05193)
  [[code]](https://github.com/adnansirajrakin/TBT-CVPR2020)
  - Adnan Siraj Rakin, Zhezhi He, and Deliang Fan. *CVPR*, 2020.

- How to Inject Backdoors with Better Consistency: Logit Anchoring on Clean Data.
  [[pdf]](https://arxiv.org/pdf/2109.01300.pdf)
  - Zhiyuan Zhang, Lingjuan Lyu, Weiqiang Wang, Lichao Sun, and Xu Sun. *ICLR*, 2022.

 
 #### Structure-modified Attack
- DeepPayload: Black-box Backdoor Attack on Deep Learning Models through Neural Payload Injection.
  [[pdf]](https://arxiv.org/pdf/2101.06896.pdf)
  - Yuanchun Li, Jiayi Hua, Haoyu Wang, Chunyang Chen, and Yunxin Liu. *ICSE*, 2021.
 
- An Embarrassingly Simple Approach for Trojan Attack in Deep Neural Networks.
  [[pdf]](https://arxiv.org/pdf/2006.08131.pdf)
  [[code]](https://github.com/trx14/TrojanNet)
  - Ruixiang Tang, Mengnan Du, Ninghao Liu, Fan Yang, and Xia Hu. *KDD*, 2020.
  
</details>

## Security Conferences
### S&P22
- SoK: How Robust is Image Classification Deep Neural Network Watermarking?
  [[pdf]](https://arxiv.org/pdf/2108.04974.pdf)

### Security22

### CCS22

### NDSS22
- DeepSight: Mitigating Backdoor Attacks in Federated Learning Through Deep Model Inspection.
  [[pdf]](https://arxiv.org/pdf/2201.00763.pdf)
  - Phillip Rieger, Thien Duc Nguyen, Markus Miettinen, and Ahmad-Reza Sadeghi. *NDSS*, 2022.
  - model filtering approach for mitigating backdoor attacks

- ATTEQ-NN: Attention-based QoE-aware Evasive Backdoor Attacks

- Get a Model! Model Hijacking Attack Against Machine Learning Models
  [[pdf]](https://arxiv.org/pdf/2111.04394.pdf)
  - Ahmed Salem Michael Backes Yang Zhang
  -  The adversary aims to hijack a target model to execute a different task than its original one without the model owner noticing.

### S&P21
- Detecting AI Trojans Using Meta Neural Analysis.
  [[pdf]](https://arxiv.org/pdf/1910.03137.pdf)
  - Xiaojun Xu, Qi Wang, Huichen Li, Nikita Borisov, Carl A. Gunter, and Bo Li. *IEEE S&P*, 2021.
  - prior work impractical assumption: (1) ''all-to-one'' attack is easy to detect, (2) white-box access to the model, (3) clean-data and clean-labell backdoor attack is difficult to detect
  - black-box access to the model, no need training data, need clean data
  - experiments cover CV, NLP, speech, tabular
  - including a brief survey

### Security21
- FLGUARD: Secure and Private Federated Learning.
  [[pdf]](https://arxiv.org/pdf/2101.02281.pdf)
  - Thien Duc Nguyen, Phillip Rieger, Hossein Yalame, Helen Möllering, Hossein Fereidooni, Samuel Marchal, Markus Miettinen, Azalia Mirhoseini, Ahmad-Reza Sadeghi, Thomas Schneider, and Shaza Zeitouni. arXiv, 2021.

- Explanation-Guided Backdoor Poisoning Attacks Against Malware Classifiers
  [[pdf]](https://www.usenix.org/conference/usenixsecurity21/presentation/severi)

- Graph Backdoor
  [[pdf]](https://www.usenix.org/conference/usenixsecurity21/presentation/xi)

- Entangled Watermarks as a Defense against Model Extraction
  [[pdf]](https://www.usenix.org/system/files/sec21-jia.pdf)

### CCS21
- AI-Lancet: Locating Error-inducing Neurons to Optimize Neural Networks
  [[pdf]](https://dl.acm.org/doi/abs/10.1145/3460120.3484818)

- Hidden Backdoors in Human-Centric Language Models
  [[pdf]](https://arxiv.org/pdf/2105.00164.pdf)

- Backdoor Pre-trained Models Can Transfer to All
  [[pdf]](https://arxiv.org/pdf/2111.00197.pdf)


### NDSS21

### SP20
- Humpty Dumpty: Controlling Word Meanings via Corpus Poisoning
  [[pdf]](https://arxiv.org/pdf/2001.04935.pdf)

### Security20

### ccs20
- Composite Backdoor Attack for Deep Neural Network by Mixing Existing Benign Features
  [[pdf]](https://dl.acm.org/doi/pdf/10.1145/3372297.3423362)

## Attack and Defense Towards Other Paradigms and Tasks
### Collaborative Learning

- DeepSight: Mitigating Backdoor Attacks in Federated Learning Through Deep Model Inspection.
  [[pdf]](https://arxiv.org/pdf/2201.00763.pdf)
  - Phillip Rieger, Thien Duc Nguyen, Markus Miettinen, and Ahmad-Reza Sadeghi. *NDSS*, 2022.
  - model filtering approach for mitigating backdoor attacks

- Defending Label Inference and Backdoor Attacks in Vertical Federated Learning.
  [[pdf]](https://arxiv.org/pdf/2112.05409.pdf)
  - Yang Liu, Zhihao Yi, Yan Kang, Yuanqin He, Wenhan Liu, Tianyuan Zou, and Qiang Yang. *AAAI*, 2022.

- CRFL: Certifiably Robust Federated Learning against Backdoor Attacks.
  [[pdf]](https://arxiv.org/pdf/2106.08283.pdf)
  - Chulin Xie, Minghao Chen, Pin-Yu Chen, and Bo Li. *ICML*, 2021.

- Curse or Redemption? How Data Heterogeneity Affects the Robustness of Federated Learning.
  [[pdf]](https://arxiv.org/pdf/2102.00655.pdf)
  - Syed Zawad, Ahsan Ali, Pin-Yu Chen, Ali Anwar, Yi Zhou, Nathalie Baracaldo, Yuan Tian, and Feng Yan. *AAAI*, 2021.

- Attack of the Tails: Yes, You Really Can Backdoor Federated Learning.
  [[pdf]](https://arxiv.org/pdf/2007.05084.pdf)
  - Hongyi Wang, Kartik Sreenivasan, Shashank Rajput, Harit Vishwakarma, Saurabh Agarwal, Jy-yong Sohn, Kangwook Lee, and Dimitris Papailiopoulos. *NeurIPS*, 2020.
  
- DBA: Distributed Backdoor Attacks against Federated Learning.
  [[pdf]](https://openreview.net/pdf?id=rkgyS0VFvr)
  - Chulin Xie, Keli Huang, Pinyu Chen, and Bo Li. *ICLR*, 2020.
  
- Defending Against Backdoors in Federated Learning with Robust Learning Rate.
  [[pdf]](https://arxiv.org/pdf/2007.03767.pdf)
  - Mustafa Safa Ozdayi, Murat Kantarcioglu, and Yulia R. Gel. *AAAI*, 2021.


- The Limitations of Federated Learning in Sybil Settings.
  [[pdf]](https://www.cs.ubc.ca/~bestchai/papers/foolsgold-raid2020.pdf)
  [[extension]](https://arxiv.org/pdf/1808.04866.pdf)
  [[code]](https://github.com/DistributedML/FoolsGold)
  - Clement Fung, Chris J.M. Yoon, and Ivan Beschastnikh. *RAID*, 2020 (arXiv, 2018).

- BEAS: Blockchain Enabled Asynchronous & Secure Federated Machine Learning.
  [[pdf]](https://arxiv.org/pdf/2202.02817.pdf)
  - Arup Mondal, Harpreet Virk, and Debayan Gupta. *AAAI Workshop*, 2022.
  
- Backdoor Attacks and Defenses in Feature-partitioned Collaborative Learning.
  [[pdf]](https://arxiv.org/pdf/2007.03608.pdf)
  - Yang Liu, Zhihao Yi, and Tianjian Chen. *ICML Workshop*, 2020.

- Can You Really Backdoor Federated Learning?
  [[pdf]](https://arxiv.org/pdf/1911.07963.pdf)
  - Ziteng Sun, Peter Kairouz, Ananda Theertha Suresh, and H. Brendan McMahan. *NeurIPS Workshop*, 2019.

- Client-Wise Targeted Backdoor in Federated Learning.
  [[pdf]](https://arxiv.org/pdf/2203.08689.pdf)
  - Gorka Abad, Servio Paguada, Stjepan Picek, Víctor Julio Ramírez-Durán, and Aitor Urbieta. arXiv, 2022.

- Backdoor Defense in Federated Learning Using Differential Testing and Outlier Detection.
  [[pdf]](https://arxiv.org/pdf/2202.11196.pdf)
  - Yein Kim, Huili Chen, and Farinaz Koushanfar. arXiv, 2022.

- ARIBA: Towards Accurate and Robust Identification of Backdoor Attacks in Federated Learning.
  [[pdf]](https://arxiv.org/pdf/2202.04311.pdf)
  - Yuxi Mi, Jihong Guan, and Shuigeng Zhou. arXiv, 2022.
  - backdoor attacks are discernible by the filters of CNN layers
  - unsupervised anomaly detection to evaluate the pre-processed filters and calculate an anomaly score for each client

- Low-Loss Subspace Compression for Clean Gains against Multi-Agent Backdoor Attacks.
  [[pdf]](https://arxiv.org/pdf/2203.03692.pdf)
  - Siddhartha Datta and Nigel Shadbolt. arXiv, 2022.

- Backdoors Stuck at The Frontdoor: Multi-Agent Backdoor Attacks That Backfire.
  [[pdf]](https://arxiv.org/pdf/2201.12211.pdf)
  - Siddhartha Datta and Nigel Shadbolt. arXiv, 2022.

- Federated Unlearning with Knowledge Distillation.
  [[pdf]](https://arxiv.org/pdf/2201.09441.pdf)
  - Chen Wu, Sencun Zhu, and Prasenjit Mitra. arXiv, 2022.
  - 6 pages
  - knowledge distillation is used to recover accuracy

```diff
unlearning & KD
```

- Model Transferring Attacks to Backdoor HyperNetwork in Personalized Federated Learning.
  [[pdf]](https://arxiv.org/pdf/2201.07063.pdf)
  - Phung Lai, NhatHai Phan, Abdallah Khreishah, Issa Khalil, and Xintao Wu. arXiv, 2022.

- Backdoor Attacks on Federated Learning with Lottery Ticket Hypothesis.
  [[pdf]](https://arxiv.org/pdf/2109.10512.pdf)
  - Zihang Zou, Boqing Gong, and Liqiang Wang. arXiv, 2021.

- On Provable Backdoor Defense in Collaborative Learning.
  [[pdf]](https://arxiv.org/pdf/2101.08177.pdf)
  - Ximing Qiao, Yuhua Bai, Siping Hu, Ang Li, Yiran Chen, and Hai Li. arXiv, 2021.

- SparseFed: Mitigating Model Poisoning Attacks in Federated Learning with Sparsification.
  [[pdf]](https://arxiv.org/pdf/2112.06274.pdf)
  - Ashwinee Panda, Saeed Mahloujifar, Arjun N. Bhagoji, Supriyo Chakraborty, and Prateek Mittal. arXiv, 2021.

- Robust Federated Learning with Attack-Adaptive Aggregation.
  [[pdf]](https://arxiv.org/pdf/2102.05257.pdf)
  [[code]](https://github.com/cpwan/Attack-Adaptive-Aggregation)
  - Ching Pui Wan, and Qifeng Chen. arXiv, 2021.

- Meta Federated Learning.
  [[pdf]](https://arxiv.org/pdf/2102.05561.pdf)
  - Omid Aramoon, Pin-Yu Chen, Gang Qu, and Yuan Tian. arXiv, 2021.

- FLGUARD: Secure and Private Federated Learning.
  [[pdf]](https://arxiv.org/pdf/2101.02281.pdf)
  - Thien Duc Nguyen, Phillip Rieger, Hossein Yalame, Helen Möllering, Hossein Fereidooni, Samuel Marchal, Markus Miettinen, Azalia Mirhoseini, Ahmad-Reza Sadeghi, Thomas Schneider, and Shaza Zeitouni. arXiv, 2021.

```diff
USENIX Security 21
```

- Toward Robustness and Privacy in Federated Learning: Experimenting with Local and Central Differential Privacy.
  [[pdf]](https://arxiv.org/pdf/2009.03561.pdf)
  - Mohammad Naseri, Jamie Hayes, and Emiliano De Cristofaro. arXiv, 2020.

- Backdoor Attacks on Federated Meta-Learning. 
  [[pdf]](https://arxiv.org/pdf/2006.07026.pdf)
  - Chien-Lun Chen, Leana Golubchik, and Marco Paolieri. arXiv, 2020. 

- Dynamic backdoor attacks against federated learning.
  [[pdf]](https://arxiv.org/pdf/2011.07429.pdf)
  - Anbu Huang. arXiv, 2020.

- Federated Learning in Adversarial Settings.
  [[pdf]](https://arxiv.org/pdf/2010.07808.pdf)
  - Raouf Kerkouche, Gergely Ács, and Claude Castelluccia. arXiv, 2020.



### Transfer Learning

- Anti-Distillation Backdoor Attacks: Backdoors Can Really Survive in Knowledge Distillation.
  [[pdf]](https://dl.acm.org/doi/pdf/10.1145/3474085.3475254)
  - Yunjie Ge, Qian Wang, Baolin Zheng, Xinlu Zhuang, Qi Li, Chao Shen, and Cong Wang. *ACM MM*, 2021.

- Hidden Trigger Backdoor Attacks.
  [[pdf]](https://arxiv.org/pdf/1910.00033.pdf)
  [[code]](https://github.com/UMBCvision/Hidden-Trigger-Backdoor-Attacks)
  - Aniruddha Saha, Akshayvarun Subramanya, and Hamed Pirsiavash. *AAAI*, 2020.

- Weight Poisoning Attacks on Pre-trained Models.
  [[pdf]](https://arxiv.org/pdf/2004.06660.pdf)
  [[code]](https://github.com/neulab/RIPPLe)
  - Keita Kurita, Paul Michel, and Graham Neubig. *ACL*, 2020.

- Latent Backdoor Attacks on Deep Neural Networks.
  [[pdf]](http://people.cs.uchicago.edu/~huiyingli/publication/fr292-yaoA.pdf)
  - Yuanshun Yao, Huiying Li, Haitao Zheng and Ben Y. Zhao. *CCS*, 2019.
  
- Red Alarm for Pre-trained Models: Universal Vulnerabilities by Neuron-Level Backdoor Attacks.
  [[pdf]](https://arxiv.org/pdf/2101.06969.pdf)
  [[code]](https://github.com/thunlp/NeuBA)
  - Zhengyan Zhang, Guangxuan Xiao, Yongwei Li, Tian Lv, Fanchao Qi, Zhiyuan Liu, Yasheng Wang, Xin Jiang, and Maosong Sun. arXiv, 2021.

### Malware Detection

- Explanation-Guided Backdoor Poisoning Attacks Against Malware Classifiers.
  [[pdf]](https://arxiv.org/pdf/2003.01031.pdf)
  - Giorgio Severi, Jim Meyer, Scott Coull, and Alina Oprea. *USENIX Security*, 2021.

- Jigsaw Puzzle: Selective Backdoor Attack to Subvert Malware Classifiers.
  [[pdf]](https://arxiv.org/pdf/2202.05470.pdf)
  - Limin Yang, Zhi Chen, Jacopo Cortellazzi, Feargus Pendlebury, Kevin Tu, Fabio Pierazzi, Lorenzo Cavallaro, and Gang Wang. arXiv, 2022.


## Discussion and Evaluation
- Backdoor Defense via Decoupling the Training Process.
  [[pdf]](https://openreview.net/pdf?id=TySnJ-0RdKI)
  [[code]](https://github.com/SCLBD/DBD)
  - Kunzhe Huang, Yiming Li, Baoyuan Wu, Zhan Qin, and Kui Ren. *ICLR*, 2022.

- How to Inject Backdoors with Better Consistency: Logit Anchoring on Clean Data.
  [[pdf]](https://openreview.net/pdf?id=Bn09TnDngN)
  - Zhiyuan Zhang, Lingjuan Lyu, Weiqiang Wang, Lichao Sun, and Xu Sun. *ICLR*, 2022.

- TROJANZOO: Everything You Ever Wanted to Know about Neural Backdoors (But were Afraid to Ask).
  [[pdf]](https://arxiv.org/pdf/2012.09302.pdf)
  [[code]](https://github.com/ain-soph/trojanzoo)
  - Ren Pang, Zheng Zhang, Xiangshan Gao, Zhaohan Xi, Shouling Ji, Peng Cheng, and Ting Wang. *EuroS&P*, 2022.

- Defending against Model Stealing via Verifying Embedded External Features.
  [[pdf]](https://www.researchgate.net/publication/356717751_Defending_against_Model_Stealing_via_Verifying_Embedded_External_Features)
  [[code]](https://github.com/zlh-thu/StealingVerification) 
  - Yiming Li, Linghui Zhu, Xiaojun Jia, Yong Jiang, Shu-Tao Xia, and Xiaochun Cao. *AAAI*, 2022. (Discuss the limitations of using backdoor attacks for model watermarking)

- Susceptibility & Defense of Satellite Image-trained Convolutional Networks to Backdoor Attacks.
  [[link]](https://www.sciencedirect.com/science/article/pii/S0020025522004248)
  - Ethan Brewer, Jason Lin, and Dan Runfola. *Information Sciences*, 2021.

- Data-Efficient Backdoor Attacks.
  [[pdf]](https://arxiv.org/pdf/2204.12281.pdf)
  [[code]](https://github.com/xpf/Data-Efficient-Backdoor-Attacks)
  - Pengfei Xia, Ziqiang Li, Wei Zhang, and Bin Li. *IJCAI*, 2022.


- Excess Capacity and Backdoor Poisoning.
  [[pdf]](https://arxiv.org/pdf/2109.00685.pdf)
  - Naren Sarayu Manoj and Avrim Blum. *NeurIPS*, 2021.

- Just How Toxic is Data Poisoning? A Unified Benchmark for Backdoor and Data Poisoning Attacks.
  [[pdf]](https://arxiv.org/pdf/2006.12557.pdf)
  [[code]](https://github.com/aks2203/poisoning-benchmark)
  - Avi Schwarzschild, Micah Goldblum, Arjun Gupta, John P Dickerson, and Tom Goldstein. *ICML*, 2021.

- Rethinking the Backdoor Attacks' Triggers: A Frequency Perspective.
  [[pdf]](https://arxiv.org/pdf/2104.03413.pdf)
  - Yi Zeng, Won Park, Z. Morley Mao, and Ruoxi Jia. *ICCV*, 2021.

- Can Optical Trojans Assist Adversarial Perturbations?
  [[pdf]](https://openaccess.thecvf.com/content/ICCV2021W/AROW/papers/Boloor_Can_Optical_Trojans_Assist_Adversarial_Perturbations_ICCVW_2021_paper.pdf)
  - Adith Boloor, Tong Wu, Patrick Naughton, Ayan Chakrabarti, Xuan Zhang, and Yevgeniy Vorobeychik. *ICCV Workshop*, 2021.

- On the Trade-off between Adversarial and Backdoor Robustness.
  [[pdf]](https://papers.nips.cc/paper/2020/file/8b4066554730ddfaa0266346bdc1b202-Paper.pdf)
  - Cheng-Hsin Weng, Yan-Ting Lee, and Shan-Hung Wu. *NeurIPS*, 2020.

- A Tale of Evil Twins: Adversarial Inputs versus Poisoned Models.
  [[pdf]](https://arxiv.org/pdf/1911.01559.pdf)
  [[code]](https://github.com/alps-lab/imc)
  - Ren Pang, Hua Shen, Xinyang Zhang, Shouling Ji, Yevgeniy Vorobeychik, Xiapu Luo, Alex Liu, and Ting Wang. *CCS*, 2020.

- Systematic Evaluation of Backdoor Data Poisoning Attacks on Image Classiﬁers.
  [[pdf]](https://arxiv.org/pdf/2004.11514.pdf)
  - Loc Truong, Chace Jones, Brian Hutchinson, Andrew August, Brenda Praggastis, Robert Jasper, Nicole Nichols, and Aaron Tuor. *CVPR Workshop*, 2020.

- On Evaluating Neural Network Backdoor Defenses.
  [[pdf]](https://arxiv.org/pdf/2010.12186.pdf)
  - Akshaj Veldanda, and Siddharth Garg. *NeurIPS Workshop*, 2020.

- Planting Undetectable Backdoors in Machine Learning Models.
  [[pdf]](https://arxiv.org/pdf/2204.06974.pdf)
  - Shafi Goldwasser, Michael P. Kim, Vinod Vaikuntanathan, and Or Zamir. arXiv, 2022.

- Towards A Critical Evaluation of Robustness for Deep Learning Backdoor Countermeasures.
  [[pdf]](https://arxiv.org/pdf/2204.06273.pdf)
  - Huming Qiu, Hua Ma, Zhi Zhang, Alsharif Abuadbba, Wei Kang, Anmin Fu, and Yansong Gao. arXiv, 2022.


- Neural Network Trojans Analysis and Mitigation from the Input Domain.
  [[pdf]](https://arxiv.org/pdf/2202.06382.pdf)
  - Zhenting Wang, Hailun Ding, Juan Zhai, and Shiqing Ma. arXiv, 2022.

- Widen The Backdoor To Let More Attackers In.
  [[pdf]](https://arxiv.org/pdf/2110.04571.pdf)
  - Siddhartha Datta, Giulio Lovisotto, Ivan Martinovic, and Nigel Shadbolt. arXiv, 2021.

- Backdoor Learning Curves: Explaining Backdoor Poisoning Beyond Influence Functions.
  [[pdf]](https://arxiv.org/pdf/2106.07214.pdf)
  - Antonio Emanuele Cinà, Kathrin Grosse, Sebastiano Vascon, Ambra Demontis, Battista Biggio, Fabio Roli, and Marcello Pelillo. arXiv, 2021.

- Rethinking the Trigger of Backdoor Attack.
  [[pdf]](https://arxiv.org/pdf/2004.04692.pdf)
  - Yiming Li, Tongqing Zhai, Baoyuan Wu, Yong Jiang, Zhifeng Li, and Shutao Xia. arXiv, 2020.      

- Poisoned Classifiers are Not Only Backdoored, They are Fundamentally Broken.
  [[pdf]](https://arxiv.org/pdf/2010.09080.pdf)
  [[code]](https://github.com/locuslab/breaking-poisoned-classifier)
  - Mingjie Sun, Siddhant Agarwal, and J. Zico Kolter. *ICLR Workshop*, 2021.

- Effect of Backdoor Attacks over the Complexity of the Latent Space Distribution.
  [[pdf]](https://arxiv.org/pdf/2012.01931.pdf)
  [[code]](https://github.com/henrychacon/Backdoor_attacks/tree/main/D-Vine_copula_auto_encoder)
  - Henry D. Chacon, and Paul Rad. arXiv, 2020.

- Noise-response Analysis for Rapid Detection of Backdoors in Deep Neural Networks.
  [[pdf]](https://arxiv.org/pdf/2008.00123.pdf)
  - N. Benjamin Erichson, Dane Taylor, Qixuan Wu, and Michael W. Mahoney. arXiv, 2020.

## Backdoor Attack for Positive Purposes
- Neural Network Surgery: Injecting Data Patterns into Pre-trained Models with Minimal Instance-wise Side Effects.
  [[pdf]](https://aclanthology.org/2021.naacl-main.430.pdf) 
  - Zhiyuan Zhang, Xuancheng Ren, Qi Su, Xu Sun and Bin He. *NAACL-HLT*, 2021.

- What Do You See? Evaluation of Explainable Artificial Intelligence (XAI) Interpretability through Neural Backdoors.
  [[pdf]](https://arxiv.org/pdf/2009.10639.pdf)
  - Yi-Shan Lin, Wen-Chuan Lee, and Z. Berkay Celik. *KDD*, 2021.

- Using Honeypots to Catch Adversarial Attacks on Neural Networks.
  [[pdf]](https://arxiv.org/pdf/1904.08554.pdf)
  - Shawn Shan, Emily Wenger, Bolun Wang, Bo Li, Haitao Zheng, Ben Y. Zhao. *CCS*, 2020. (**Note:** Unfortunately, it was bypassed by Nicholas Carlini most recently. [[arXiv]](https://arxiv.org/pdf/2009.10975.pdf))
  
- Turning Your Weakness into a Strength: Watermarking Deep Neural Networks by Backdooring.
  [[pdf]](https://arxiv.org/pdf/1802.04633.pdf)
  [[code]](https://github.com/adiyoss/WatermarkNN)
  - Yossi Adi, Carsten Baum, Moustapha Cisse, Benny Pinkas, and Joseph Keshet. *USENIX Security*, 2018. 

- Open-sourced Dataset Protection via Backdoor Watermarking.
  [[pdf]](https://arxiv.org/pdf/2010.05821.pdf)
  - Yiming Li, Ziqi Zhang, Jiawang Bai, Baoyuan Wu, Yong Jiang, and Shu-Tao Xia. *NeurIPS Workshop*, 2020.

- Protecting Deep Cerebrospinal Fluid Cell Image Processing Models with Backdoor and Semi-Distillation.
  [[link]](https://ieeexplore.ieee.org/abstract/document/9647115)
  - FangQi Li, Shilin Wang, and Zhenhai Wang. *DICTA*, 2021.

- Debiasing Backdoor Attack: A Benign Application of Backdoor Attack in Eliminating Data Bias.
  [[pdf]](https://arxiv.org/pdf/2202.10582.pdf)
  - Shangxi Wu, Qiuyang He, Yi Zhang, and Jitao Sang. arXiv, 2022.

- Watermarking Graph Neural Networks based on Backdoor Attacks.
  [[pdf]](https://arxiv.org/pdf/2110.11024.pdf)
  - Jing Xu and Stjepan Picek. arXiv, 2021.

- CoProtector: Protect Open-Source Code against Unauthorized Training Usage with Data Poisoning.
  [[pdf]](https://arxiv.org/pdf/2110.12925.pdf)
  - Zhensu Sun, Xiaoning Du, Fu Song, Mingze Ni, and Li Li. arXiv, 2021.

- What Do Deep Nets Learn? Class-wise Patterns Revealed in the Input Space.
  [[pdf]](https://arxiv.org/pdf/2101.06898.pdf)
  - Shihao Zhao, Xingjun Ma, Yisen Wang, James Bailey, Bo Li, and Yu-Gang Jiang. arXiv, 2021.

- A Stealthy and Robust Fingerprinting Scheme for Generative Models.
  [[pdf]](https://arxiv.org/pdf/2106.11760.pdf)
  - Guanlin Li, Shangwei Guo, Run Wang, Guowen Xu, and Tianwei Zhang. arXiv, 2021.

- Towards Probabilistic Verification of Machine Unlearning.
  [[pdf]](https://arxiv.org/pdf/2003.04247.pdf)
  [[code]](https://github.com/inspire-group/unlearning-verification)
  - David Marco Sommer, Liwei Song, Sameer Wagh, and Prateek Mittal. arXiv, 2020. 

