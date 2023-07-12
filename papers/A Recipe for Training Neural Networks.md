by Andrej Karpathy

### 1. Become one with the data

- not touch any neural net code at all and instead begin by thoroughly inspecting your data.
- I look for data imbalances and biases. I will typically also pay attention to my own process for classifying the data, which hints at the kinds of architectures we’ll eventually explore. 
	- are very local features enough or do we need global context? 
	- How much variation is there and what form does it take? 
	- What variation is spurious and could be preprocessed out? 
	- Does spatial position matter or do we want to average pool it out? 
	- How much does detail matter and how far could we afford to downsample the images? 
	- How noisy are the labels?

- look at your network (mis)predictions and understand where they might be coming from. And if your network is giving you some prediction that doesn’t seem consistent with what you’ve seen in the data, something is off.
- write some simple code to search/filter/sort by whatever you can think of (e.g. type of label, size of annotations, number of annotations, etc.) and visualize their distributions and the outliers along any axis. *The outliers especially almost always uncover some bugs in data quality or preprocessing.*


#knowledge  