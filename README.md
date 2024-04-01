# ML4SCI GSOC GENIE Task
## Specific Task 1
The jet images captured by the different sensors are of extremely large magnitude. This makes it extremely difficult to label all the data. But this labeled data is necessary for a multitude of Deep Learning tasks. One way to tackle this problem is to use Semi-Supervised or Un-Supervised learning where the model is given no or a few labelled data and it learns to cluster similar data together. In this task, we tackle the same problem as Common Task 2. We classify the graph but here we use contrastive learning to learn the graph representation. What essentially happens is we generate two positive pairs of the same graph, i.e. we apply augmentation on the graph and generate two samples. Our main goal here is to maximize agreement between these positive pairs and minimize between negative samples, which are images of different Jets.

## Task
- Classify the quark/gluon data with a model that learns data representation with a contrastive loss.
- Evaluate the classification performance on a test dataset.

## Training

The following parameters were used to train the Contrastive Model to learn Graph representation:
```
Learning rate: 0.01
Optimizer: Adam
Loss: InfoNCE
Temperature: 0.2
mode: Local-to-Local
Epochs: 30
```
The following parameters were used to train the Classification Model :
```
Learning rate: 0.01
Optimizer: Adam
Loss: Cross entropy
Epochs: 20
```

## Result

Data  | Accuracy |
------------- | ------------- 
Training Data  | 67.5% | 
Test Data | 70% | 

## Conclusion

The model's accuracy is 70% which is not the best. There are a multitude of reasons for that.

- One big problem is graph-level representation. Although, I have used global pooling to get a graph-level representation that is not the best way.

- We only consider an extremely small subset of the actual data due to memory issues which may cause data imbalance which stops the model from learning properly.

- Another problem is the graph representation isn't being learned well. Many possible reasons can be for this such as the architecture may not be right, the parameter tuning needs to be done well, etc. Further Research into this is required. 

- When constructing the contrastive learning architecture other Graph models may be used such as GAT, GraphSage, etc  to learn the representation. Each of these models will learn a different representation for the node which may be better or worse but may increase the complexity of the model which may be computationally inefficient for larger datasets and graphs or also decrease.
