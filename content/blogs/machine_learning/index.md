---
title: Machine Learning
summary: An advanced introduction.
date: 2021-03-25
math: true
tags:
- Other
diagram: true
image:
  placement: 3
  # caption: 'Image credit: [**John Moeses Bauan**](https://unsplash.com/photos/OGZtQF8iC0g)'
---

# Interpretable Machine Learning: some fun fact.
> The opinions are from Ms Cynthia Rudin. 
- You can generally find an interpretable ML model that is as accurate as any black box model. 
- It has become clear that people don't know this. 
- DON'T USE BLACK BOX MODEL FOR HIGH-STAKE APPLICATIONS.
- There is no scientific evidence for a tradeoff between interpretability and accuracy.


# PyTorch
## Tensors
> A specialized data structure encodes input / output / models' parameters. It's similar to numpy's arrays, but it can run on GPU or other specialized hardware to accelerate computing. 

### commands (very similar to numpy)
- creating a tensor
    ```
    torch.tensor()
    torch.from_numpy()
    torch.ones_like()
    torch.rand_like()
    shape = (2, 3,)
    torch.rand(shape)
    ```
- tensor attributes
    ```
    tensor.shape
    tensor.dtype
    tensor.device
    ```
- tensor operation
transposing, indexing, slicing, etc

- multiplying tensors (element-wise)
    ```
    tensor.mul(tensor)
    tensor * tensor
    ```
- In-place operations
operation that have a underline suffix are in place. (change x)
    ```
    tensor.add_(5)
    x = x + 5
    ```
### Bridge with Numpy
Tensors on the CPU and numpy array can share their underlying memory location, and changing one will change the other.
```
t = torch.ones(5)
n = t.numpy()
t.add_(1)
print(n)
print(t)
```

## AUTOGRAD
torch.autograd is PyTorch’s automatic differentiation engine that powers neural network training. 

### BACKGROUND
Neural networks (NNs) are a collection of nested functions that are executed on some input data. These functions are defined by parameters (consisting of weights and biases), which in PyTorch are stored in tensors.
- Forward propagation
- Backward propagation

### Usage in PyTorch
1. Let’s take a look at a single training step. For this example, we load a pretrained resnet18 model from torchvision. We create a random data tensor to represent a single image with 3 channels, and height & width of 64, and its corresponding label initialized to some random values.
    ```
    import torch, torchvision
    model = torchvision.models.resnet18(pretrained=True)
    data = torch.rand(1, 3, 64, 64)
    labels = torch.rand(1, 1000)
    ```
2. Next, we run the input data through the model through each of its layers to make a prediction. This is the forward pass.
    ```
    prediction = model(data) # forward pass
    ```
3. We use the model’s prediction and the corresponding label to calculate the error (loss). The next step is to backpropagate this error through the network. Backward propagation is kicked off when we call .backward() on the error tensor. Autograd then calculates and stores the gradients for each model parameter in the parameter’s .grad attribute.  
    ```
    loss = (prediction - labels).sum()
    loss.backward() # backward pass
    ```
4. Next, we load an optimizer, in this case SGD with a learning rate of 0.01 and momentum of 0.9. We register all the parameters of the model in the optimizer.
    ```
    optim = torch.optim.SGD(model.parameters(), lr=1e-2, momentum=0.9)
    ```
5. Finally, we call .step() to initiate gradient descent. The optimizer adjusts each parameter by its gradient stored in .grad.
    ```
    optim.step() # gradient descent
    ```
6. At this point, you have everything you need to train your neural network. The below sections detail the workings of autograd - feel free to skip them.

See the [working details of autograd](https://pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html#sphx-glr-beginner-blitz-autograd-tutorial-py)

## Neural Network
> torch.nn
### Typical training procedure
- Define the neural network that has some learnable parameters (or weights) 
- Iterate over a dataset of inputs 
- Process input through the network
- Compute the loss (how far is the output from being correct)
- Propagate gradients back into the network’s parameters
- Update the weights of the network, typically using a simple update rule:
> weight = weight - learning_rate * gradient

## torchvision.datasets
- The MNIST database (Modified National Institute of Standards and Technology database[1]) is a large database of handwritten digits that is commonly used for training various image processing systems.

### data structure
- torch.utils.data.DataLoader
> At the heart of PyTorch data loading utility is the torch.utils.data.DataLoader class. It represents a Python iterable over a datasets
```
DataLoader(dataset, batch_size=1, shuffle=False, sampler=None,
           batch_sampler=None, num_workers=0, collate_fn=None,
           pin_memory=False, drop_last=False, timeout=0,
           worker_init_fn=None, *, prefetch_factor=2,
           persistent_workers=False)
```
- push data onto device 
when we configure the nn, we would specify its device.
```
net = net.to(device)
```
And we surely need to move data to the same device.
```
for batch_idx, (data, target) in enumerate(train_loader):
    data = data.to(device)
    target = target.to(device)
    ......
```
Thus we can run the data on the device we want.




### Evaluation mode  
- The difference between train mode (default) and evaluation mode only makes sense when you use dropout layer in PyTorch.
#### How to evaluate multi-class models?
The NN will generate a n(class number) dimension output, with prob on each class. We can just find the max value and the prediction would be the consistent label. 
```
_, prediction = torch.max(outputs.data, 1)
```


### Convergence of Neural Network
- A machine learning model reaches convergence when it achieves a state duting training in which loss settles to within an error range around the final values. In other words, a model converges when additional training will not improve the model. 

# Probabilistic Machine Learning

# Math of  Machine Learning
- Linear algebra. Multi- calculus. 







# References
[1] [Latent Variables & Expectation Maximization Algorithm](https://towardsdatascience.com/latent-variables-expectation-maximization-algorithm-fb15c4e0f32c)<br>
[2] [tensor operation](https://pytorch.org/docs/stable/torch.html)<br>
[3] [implement neural network pytorch](https://pytorch.org/tutorials/beginner/blitz/neural_networks_tutorial.html#sphx-glr-beginner-blitz-neural-networks-tutorial-py)
