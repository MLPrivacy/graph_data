- The Bash script failed due to an incorrect value assigned to the `--epsilon_rate ${er}` parameter, leading to a negative privacy budget for labels and an invalid `delta_f` in the Gaussian noise configuration. (Review A1)  

- The execution and output files of the baselines are stored in their respective `baselines` directories. (Review A2)  

- We have submitted an updated artifact to Zenodo at [https://doi.org/10.5281/zenodo.14710401](https://doi.org/10.5281/zenodo.14710401), which includes newly created Bash scripts for both DPA-GNN and the baselines. The experimental results can be reproduced using either of the following methods: (1) running the provided Bash scripts or (2) executing commands manually, as detailed below.  

### **DPA-GNN**  
(1) Running the Bash script: `run_DPA-GNN.sh`, with output in `./output_DPA-GNN/`.

(2) Running the following command, with output in `./output_results.txt`. 
```python train.py --c_rate 0.8 --layerx 10 --layery 8 --epsilon_all 8 --epsilon_rate 0.05 --dataset cora```



---

### **Baselines**  

#### **LPGNN+RR**  
**(1) Using the Bash script:**  
```bash
\baselines\LPGNN+RR> run_lpgnn_rr.sh  
```
**Output:**  `\baselines\LPGNN+RR\output_lpgnn_rr\`

**(2) Running the command manually:**  
```bash
python run_lpgnn_rr.py --dataset cora --x_steps 2 --y_steps 2 --all_eps 8 --eps_rate 0.05 --y_eps 1  
```
**Output:**  `\baselines\LPGNN+RR\output_lpgnn_rr.txt`

---

#### **RGNN+RR**  
**(1) Using the Bash script:**  
```bash
\baselines\RGNN+RR> run_rgnn_rr.sh  
```
**Output:**  `\baselines\RGNN+RR\output_rgnn_rr\`

**(2) Running the command manually:**  
```bash
python run_rgnn_rr.py --dataset cora --cols_to_group 20 --all_eps 8 --eps_rate 0.05 --y_eps 1.5 --xhops 4 --yhops 2 --num_clusters 32 --alpha 1  
```
**Output:**  `\baselines\RGNN+RR\output_rgnn_rr.txt`

---

#### **Solitude+RR**  
**(1) Using the Bash script:**  
```bash
\baselines\Solitude+RR> run_solitude_rr.sh  
```
**Output:**  `\baselines\Solitude+RR\output_solitude_rr\`

**(2) Running the command manually:**  
```bash
python run_solitude_rr.py --dataset cora --cols_to_group 25 --all_eps 8 --eps_rate 0.05 --y_eps 1.5 --xhops 4 --yhops 0 --num_clusters 16 --alpha 1  
```
**Output:**  `\baselines\Solitude+RR\output_solitude_rr.txt`
