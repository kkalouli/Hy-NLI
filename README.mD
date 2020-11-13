# About

This is Hy-NLI, a hybrid NLI engine, which computes the inference relation between two sentences. It consists of a symbolic componenent, GKR4NLI, and a deep-learning component, a language
representation model. Each of those two components computes an inference label for a given pair. Based on these labels and on features of semantic nature of the pair, the hybrid
classifier determines which of the two labels should be trusted for a given pair. Find more details in our paper:

*Kalouli, A.-L., R. Crouch and V. de Paiva. 2020. Hy-NLI: a Hybrid system for Natural Language Inference. In Proceedings of COLING 2020 (link coming soon).*

If you are interested in the explaianability of our system, check out our demo paper:

*Kalouli, A.-L., R. Sevastjanova, R. Crouch, V. de Paiva and M. El-Assady. 2020. XplaiNLI: Explainable Natural Language Inferencethrough Visual Analytics. In Proceedings of COLING 2020 (link coming soon).*

Author/developer: Aikaterini-Lida Kalouli (<aikaterini-lida.kalouli@uni-konstanz.de>) and Richard Crouch (<dick.crouch@gmail.com>)

If you use this software in writing scientific papers, or you use this software in any other medium serving scientists or students (e.g. web-sites,
CD-ROMs) please include the above citation.

# Demo
If you would like to have a quick taste of how Hy-NLI looks like, check out our online demo: http://bit.ly/XplaiNLI


# License
Copyright 2020 Aikaterini-Lida Kalouli and Richard Crouch. GKR is a free-software discributed under the conditions of the Apache License 2.0, without warranty. See LICENSE file for more details. You should have received a copy of the LICENSE file with the source code. If not, please visit http://www.apache.org/licenses/ for more information. 

# Installation 

## Symbolic Component: GKR4NLI

To get the symbolic component working, you need to clone and following the installation instructions of the following repo:
 ``` git clone https://github.com/kkalouli/GKR4NLI.git ```.
 
 ## Deep-Learning Component: BERT/XLNet
 
 For the DL component, we have fine-tuned the BERT (base, uncased) and the XLNet model with the HuggingFace implementation. The fine-tuned models can be downloaded from
 here *https://drive.google.com/file/d/1Fd9rIgvd_T7zvt8pRxuK48lnwRgXmlor/view?usp=sharing* and here *https://drive.google.com/file/d/1RafWCQY_BMF8KRC5MkcLweNXWOd7w1kF/view?usp=sharing*  In the folder *dl_component*,
 you can find the notebooks *BERT_finetuning_NLI.ipynb* and *XLNet_finetuning_NLI.ipynb*, with which the models were fine-tuned and evaluated (the notebooks were created 
 based on the informative tutorials by *Chris McCormick and Nick Ryan. (2019, July 22). BERT Fine-Tuning Tutorial with PyTorch. Retrieved from http://www.mccormickml.com*).
 If you want to evaluate a set on our fine-tuned models, follow the instructions in the Section *Load fine-tuned model and evaluate on a given test set* of the notebooks. In the folder *dl_component*, you can also find the SICK_trial_and_train_set, on which the models were fine-tuned. 
 
 ## Hybrid Component: Hy-NLI
 
 
 
 
 
 
 which takes as input a pair and uses the fine-tuned models to classify it. You can run the script by
  ``` python get_dl_inference_decision.py premise hypothesis  ```
  e.g., ``` python get_dl_inference_decision.py "The dog is walking." "The animal is walking."  ```





# Contact
For troubleshooting, comments, ideas and discussions, please contact aikaterini-lida.kalouli(at)uni-konstanz.de or dick.crouch(at)gmail.com

