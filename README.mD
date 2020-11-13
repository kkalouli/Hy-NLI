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
 If you want to evaluate a set on our fine-tuned models, follow the instructions in the Section *Load fine-tuned model and evaluate on a given test set* of the notebooks. In the folder *dl_component*, you can also find the *SICK_trial_and_train_set.txt*, on which the models were fine-tuned. 
 
 Note that the trained models output 0 for E, 1 for C and 2 for N. 
 
 ## Hybrid Component: Hy-NLI
 ### Training the Classifier
 To train the classifier, we first have to bring the training set to the suitable format. For this, we take the following steps:
 
 1. We run GKR4NLI on our training set. Specifically, we run the main method of *InferenceComputer* on the *SICK_trial_and_train_set.txt*. This outputs two files: *SICK_trial_and_train_set_with_inference_relation.csv* and *SICK_trial_and_train_set_GKR4NLI_results.csv*. The file *SICK_trial_and_train_set_GKR4NLI_results.csv* will be used for the further processing. You can find this file within the folder *data/SICK/*. You can find the results of the other datasets in the corresponding folders.
 
 2. We run the fine-tuned DL model on *SICK_trial_and_train_set.txt* and collect the predicted labels in the file *SICK_trial_and_train_set_BERT_results.csv.* This file is also used for the further processing. You can find this file within the folder *data/SICK*. You can find the results of the other datasets in the corresponding folders.
 
3. We use the two created files to train the hybrid classifier as explained in the notebook *create_hybrid_classifier.ipynb*, found in the folder *hybrid_classifier*. The MLP classifier we have trained can also be found in the folder *hybrid_classifier*.
 
 ### Evaluating the Classifier
To evaluate the hybrid classifier on a test set, we follow the instructions explained in the notebook *create_hybrid_classifier.ipynb*. If you want to evaluate a set on our trained classifier (or reproduce our results), follow the instructions in the Section *Loading the trained classifier and evaluating on it* of the notebook. 
 

# Contact
For troubleshooting, comments, ideas and discussions, please contact aikaterini-lida.kalouli(at)uni-konstanz.de or dick.crouch(at)gmail.com

