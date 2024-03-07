# ML4SCI GSOC GENIE Task
## Specific Task 1
In Graph neural Networks one of the biggest problems is that it tends to overfit on small datasets. One way to go around this problem is to use contrastive learning. In this task, we tackle the same problem as the Common Task 2. We classify the graph but here we use contrastive learning to learn the graph representation. What essentially happens is we generate two positive pairs of the same graph, i.e. we apply augmentation on the graph and generate two samples. Our main goal here is to maximize agreement between these positive pairs and minimize between negative samples.

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
Training Data  | 0.6850 | 
Test Data | 0.6800 | 

## Conclusion

The model's accuracy is 68% which is not the best. There are a multitude of reasons for that.

- One big problem is graph-level representation. Although, I have used global pooling to get a graph-level representation that is not the best way.

- We only consider an extremely small subset of the actual data due to memory issues which may cause data imbalance which stops the model from learning properly.

- Another problem is the graph representation itself. When we convert the image to graph the node features or deciding the edge features is an important task. Here, I take only the value of the 3 channels(Tracks, ECAL or HCAL) as node features but in related work, people have taken the position of the pixels as node features or we can take momentum, etc.

- When constructing the contrastive learning model other Graph models may be used such as GAT, GraphSage, or Edge Convolution to learn the representation. Each of these models will learn a better representation of the neighbor but would increase the complexity of the model which may be computationally inefficient for larger datasets and graphs.
