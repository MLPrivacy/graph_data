We thank all the reviewers for their constructive feedback. We have addressed the issues in the Bash script and improved the artifact as follows: 
- The Bash script failed because the `--epsilon_rate` parameter should take the value of `${eps_r}`, but it was incorrectly assigned the computed value of `${er}`, resulting in a negative privacy budget for labels and an invalid `delta_f` in the Gaussian noise configuration. (Review A1)

- The execution and output files for the baselines are stored in their respective `baselines` directories, with each baseline executed using the command specified in its corresponding `README`. (Review A2)

- We have submitted an updated artifact to Zenodo at [https://doi.org/10.5281/zenodo.14710401](https://doi.org/10.5281/zenodo.14710401), which includes newly created Bash scripts for both DPA-GNN and the baselines. The experimental results can be reproduced using either of the following methods: (1) running the provided Bash scripts or (2) executing commands manually, as detailed below.  

### **DPA-GNN**  
(1) Run the Bash script `run_DPA-GNN.sh`. The experimental results will be stored in `./output_DPA-GNN/`.  

(2) Execute the following command. The experimental results will be stored in `./output_results.txt`: 
```
python train.py --c_rate 0.8 --layerx 10 --layery 8 --epsilon_all 8 --epsilon_rate 0.05 --dataset cora
```

### **Baselines**  
(1) Run the Bash script `./baselines/<baseline_name>/run_<baseline_name>.sh`. The experimental results will be stored in `./baselines/<baseline_name>/output_<baseline_name>/`.  

(2) Execute the command specified in each baseline's `README`. The experimental results will be stored in `./baselines/<baseline_name>/output_<baseline_name>.txt`.  


----------------------------------
----------------------------------
这里的内容可以考虑下是否需要这么具体？
#### **LPGNN+RR**  
(1) Run the Bash script `run_lpgnn_rr.sh`. The experimental results will be stored in `./baselines/LPGNN+RR/output_lpgnn_rr/`.  

(2) Execute the following command. The experimental results will be stored in `./baselines/LPGNN+RR/output_lpgnn_rr.txt`.  
```
cd /baselines/LPGNN+RR>
python run_lpgnn_rr.py --dataset cora --x_steps 2 --y_steps 2 --all_eps 8 --eps_rate 0.05 --y_eps 1  
```

#### **RGNN+RR**  
(1) Run the Bash script `run_rgnn_rr.sh`. The experimental results will be stored in `./baselines/RGNN+RR/output_rgnn_rr/`.  

(2) Execute the following command manually. The experimental results will be stored in `./baselines/RGNN+RR/output_rgnn_rr.txt`.  
```
cd /baselines/RGNN+RR>
python run_rgnn_rr.py --dataset cora --cols_to_group 20 --all_eps 8 --eps_rate 0.05 --y_eps 1.5 --xhops 4 --yhops 2 --num_clusters 32 --alpha 1 
```

#### **Solitude+RR**  
(1) Run the Bash script `run_solitude_rr.sh`. The experimental results will be stored in `./baselines/Solitude+RR/output_solitude_rr/`.  

(2) Execute the following command. The experimental results will be stored in `./baselines/Solitude+RR/output_solitude_rr.txt`.  

```
cd /baselines/Solitude+RR>
python run_solitude_rr.py --dataset cora --x_steps 4 --y_steps 2 --all_eps 8 --eps_rate 0.05 --y_eps 2
```



We thank the reviewer for the constructive feedback. We submit an improved artifact to Zenodo at [https://doi.org/10.5281/zenodo.14710401](https://doi.org/10.5281/zenodo.14710401), which updates all instances of the `torch.load()` function by setting the `weights_only` parameter to `False`. Additionally, we create the `run_utility-privacy.sh` script, which generates results stored in the `results.csv` file. These results correspond to the data presented in Table 3 of the paper, with a subset provided below.


|Method | Dataset | $\varepsilon$  | $\varepsilon_h$ | Accuracy |
------------|-----------|-------------|-------------|-----------
DPA-GNN     |cora       |10 |5%$\varepsilon$ |78.5 +- 1.47 
DPA-GNN     |cora      |10 | 20%$\varepsilon$  |78.1 +- 1.8
Solitude+RR  |cora      |10  |5%$\varepsilon$  |62.3 +- 2.81
Solitude+RR  |cora      |10 |20%$\varepsilon$  |36.6 +- 5.07
LPGNN+RR     |cora      |10  |5%$\varepsilon$  |60.8 +- 4.02
LPGNN+RR     |cora      |10  |20%$\varepsilon$ |41.3 +- 4.03
RGNN+RR      |cora      |10  |5%$\varepsilon$  |54.8 +- 2.81
RGNN+RR      |cora      |10  |20%$\varepsilon$ |37.5 +- 3.44



————————————————————————————————————————————————————————————————————————————————————————


We sincerely appreciate the time and effort you have devoted to enhancing the quality of our artifact. Below are our detailed responses to your suggestions.

@ A7:
The installation issue with `torch-sparse` is caused by compatibility problems between the newer version of Python and the older version of Torch.
To ensure the stability of the experimental execution, we recommend running the artifact in a fixed environment. The required package configuration is as follows:
```
- Python == 3.8.18
- Torch == 2.1.0
- Torch-Geometric == 2.4.0
- Torch-Scatter == 2.1.2
- Torch-Sparse == 0.6.18
- Numpy == 1.24.4
- Pandas == 2.0.3
- Scikit-learn == 1.3.2
- Scipy == 1.8.0
```
@ A8:
We submit the updated artifact to Zenodo at https://doi.org/10.5281/zenodo.14710401. This version includes the Bash scripts for experiments [E1]-[E10], with the results stored in CSV files within the `./output` directory. Due to time constraints, we are unable to provide the scripts for generating the figures in the paper in a timely manner, and we sincerely apologize for the inconvenience caused by this delay. We will complete the remaining work as soon as possible and include the full scripts in future updates. 



