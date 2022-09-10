# Intelligent Jira Tool - Machine Learning and AI

A bug reporting system like Jira which is an Atlassian product highly popular among the software and product management community due to its robustness. Despite so, it mostly fails to identify the bugs if they are duplicates of earlier bugs or fresh new ones. As a result the software developers or maintainers face much hassle as they waste their valuable time reporting, tracking, updating, addressing, maintaining the bugs which may be duplicates and they never knew of the fact.

The newly reported bugs, if duplicates then they must be either resolved and recorded somewhere in the system and the team unknowingly waited on the resolution causing further delay in their business deliveries.

Early detecton of duplicate bugs is a real critical situation needs our attention. If we can resolve this problem at the earliest, many engineers and testers can benefit from this.

This work proposes a double-tier approach using clustering and classification, whereby it exploits Latent Dirichlet Allocation (LDA) for topic-based clustering, single and multimodal text representation using Word2Vec (W2V), FastText (FT), and Global Vectors for Word Representation (GloVe), and text similarity measure fusing Cosine and Euclidean measures. The proposed model is tested on the Eclipse dataset consisting over 80,000 bug reports, which is the amalgamation of both master and duplicate reports. This work only considers the description of the reports for detecting duplicates. The experimental results show that the proposed double-tier model achieves a recall rate of 67% for Top-N recommendations in 3 times faster computation than the conventional one-on-one classification model. 


## Action 1 - Clustering
  - Latent Dirichlet Allocation (LDA) is applied on the preprocessed master reports toform clusters.
  - Pre-trained LDA is applied on preproccesed duplicate report to find the most similar cluster in which associated master report may exist.

## Action 2 - Classification 
  - Home cluster : The duplicate report jumps into the selected Top-n cluster to find the most similar master report.
  - Finding the master report:
      * Unified similarity measure using Cosine and Euclidean similarity is used to find the similarity between single or multimodal feature vectors of a duplicate report and the master reports in the corresponding cluster individually.
      * Top-N similarities would be selected which would result in Top-N recommended master reports.
