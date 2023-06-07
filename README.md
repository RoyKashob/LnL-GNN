# Node Embedding using Mutual Information and Self-Supervision based Bi-level Aggregation


**Authors**
- [Kashob Kumar Roy](https://www.linkedin.com/in/forkkr/) 
- [Amit Roy](https://amitroy7781.github.io/)
- [Amin Ahsan Ali](http://www.cse.iub.edu.bd/faculties/53)
- [M Ashraful Amin](http://www.cse.iub.edu.bd/faculties/25) 
- [A K M Mahbubur Rahman](http://www.cse.iub.edu.bd/faculties/56)

This is a pytorch implementation of our [paper](https://arxiv.org/pdf/2104.13014.pdf) "Node Embedding using Mutual Information and Self-Supervision based Bi-level Aggregation" which has been accepted by IJCNN 2021.  Check the video presentation of our paper [here](https://youtu.be/dVAm6GgIMzQ).

## Citation

If you find our paper or repo useful then please cite our paper:

```bibtex
@article{roy2021node,
  title={Node Embedding using Mutual Information and Self-Supervision based Bi-level Aggregation},
  author={Roy, Kashob Kumar and Roy, Amit and Rahman, AKM and Amin, M Ashraful and Ali, Amin Ahsan},
  journal={arXiv preprint arXiv:2104.13014},
  year={2021}
}
```


# Abstract

Graph Neural Networks (GNNs) learn low dimensional representations of nodes by aggregating information from their neighborhood in graphs. However, traditional GNNs suffer from two fundamental shortcomings due to their local (l-hop neighborhood) aggregation scheme. First, not all nodes in the neighborhood carry relevant information for the target node. Since GNNs do not exclude noisy nodes in their neighborhood, irrelevant information gets aggregated, which reduces the quality of the representation. Second, traditional GNNs also fail to capture long-range non-local dependencies between nodes. To address these limitations, we exploit mutual information (MI) to define two types of neighborhood, 1) Local Neighborhood where nodes are densely connected within a community and each node would share higher MI with its neighbors, and 2) Non-Local Neighborhood where MI-based node clustering is introduced to assemble informative but graphically distant nodes in the same cluster. To generate node presentations, we combine the embeddings generated by bi-level aggregation - local aggregation to aggregate features from local neighborhoods to avoid noisy information and non-local aggregation to aggregate features from non-local neighborhoods. Furthermore, we leverage self-supervision learning to estimate MI with few labeled data. Finally, we show that our model significantly outperforms the state-of- the-art methods in a wide range of assortative and disassortative graphs

# LnL-GNN

![LnL-GNN](Limitations.png?raw=true "Title")

Two weaknesses of classic GNNs: i) incompetent to distinguish between relevant (enclosed by green boundary) and irrelevant nodes in l-hop local-neighborhood; ii) less effective in capturing feature information from distant but similar nodes (two green center points).


![LnL-GNN](LnLGNN.png?raw=true "Title")

![LnL-GNN](flowchart.png?raw=true "Title")

Flow chart of LnL-GNN: At the first stage, MLP, to compute SEs, and MI Estimator, E, are trained using the estimation loss L. At next stage, obtained SEs and trained E are used to define local and non-local neighborhood followed by performing the local and non-local aggregation to compute the final embeddings of nodes. And, it updates the parameters of aggregation modules by optimizing the classification cross-entropy loss. Here, M3S denotes Multi-stage Self-Supervised Sampling. Dashed Line(- - -): Pre-processed Input Propagation, Solid Line (—) : Weight Update.

# Baseline Comparison
![Baseline Comparison](comparison.png?raw=true "Title")

    Table : Comparison with Baselines: ’-’ denotes that results are not publicly available.
