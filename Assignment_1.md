# **Assignment 1**

## Questions

1. What are Channels and Kernels (according to EVA)?
2. Why should we (nearly) always use 3x3 Kernels?
3. How many times do we need to perform 3x3 convolution operation to reach 1x1 from 199x199 (show calculations)?
4. How are kernels initialized? 
5. What happens during the training of a DNN?
## Solutions

### Answer 1:- 

**Channels**

Channels are also called **feature maps.** They are basically the outcome of convolutions of kernels or feature extractors. Every channel after the first layer of a CNN will be a feature map. For example before the first layer of CNN, RGB images have 3 channels (red, green & blue).Therefore,when we provide the number of kernels or feature extractor in a convolution layer the output will be the exact channels/feature map after convolution.For example if we have 40 kernels then we will have 40 channels.

One image can be divided into many channels.

Lets take few examples :- 

1. Think of any food item. Don't think about the food but think about the ingredients that are needed to make or cook the food. So every ingredient can be thought of channel. 

2. Lets think of a song by a famous band . Don't think about the complete final song but think about different instruments that are used to make that song so good. Different instruments used can be thought as different channels.

3. At last the example of television. In television people can see various type of contents.So all contents are not present in a single channel.For every channel there is a specific type of content available.So there are many channels.

   **Each channel will contain similar type of information**





**Kernels**

Kernels are also called **filters, 3x3 matrix or feature extractor**. Kernels are used to captures the edges or gradients or small features of the image. Kernel is a small matrix which is used to extract features from an image. We generally provide the number of kernels to be used in convolution. If we provide less number of kernels then less features might will be captured so we should generally use 32 kernels or sometimes 64 kernels in medical studies.

It is used for blurring, sharpening, embossing, edge detection, and more.

We can make complex things from small features.So these kernels are used to capture very small features in an image.

Example :-  edges/gradients > textures > patterns > parts of object > object > scene

Image showing different filters is below 

![filters](https://cdn-images-1.medium.com/max/1600/1*_34EtrgYk6cQxlJ2br51HQ.gif)



### Answer 2:- 

Mostly we use 3x3 kernels. 3 is a odd number if we were considering the final pixel of the subsequent layer which was obtained after convolution of  previous layer, then it will have **symmetry around the output pixel**.From the given image below we can see that if it was a 2x2 kernel then there is no central pixel in the middle of the 2x2 matrix. If we are using 3x3 kernels then the symmetry will be achieved easily. So all of the time we select odd size sized kernels and especially only 3x3.

![kernels](https://cdn-images-1.medium.com/max/750/0*zZDxNYnURBLdxnKn.jpg)



There is another reason that **3x3 kernel takes less parameters that is only 9** whereas 5x5 will take 25 parameters. So it is better to do 3x3 convolution two times because it is similar to using a single 5x5 kernel in a convolution.At end 3x3 gives 18 parameters whereas 5x5 will give 25 parameters.So lesser the parameters, faster is the computation 

Now a days **graphics card manufacturers optimize their GPUs for 3x3 kernel** whereas other like 5x5 or 7x7 will take much more time for computation.



### Answer 3 :- 

We need to do it 99 times to reach from 199x199 to 1x1

199	x   199

197	x   197

195	x	195

193	x	193

191	x	191

189	x	189

187	x	187

185	x	185

183	x	183

181	x	181

179	x	179

177	x	177

175	x	175

173	x	173

171	x	171

169	x	169

167	x	167

165	x	165

163	x	163

161	x	161

159	x	159

157	x	157

155	x	155

153	x	153

151	x	151

149	x	149

147	x	147

145	x	145

143	x	143

141	x	141

139	x	139

137	x	137

135	x	135

133	x	133

131	x	131

129	x	129

127	x	127

125	x	125

123	x	123

121	x	121

119	x	119

117	x	117

115	x	115

113	x	113

111	x	111

109	x	109

107	x	107

105	x	105

103	x	103

101	x	101

99	x	99

97	x	97

95	x	95

93	x	93

91	x	91

89	x	89

87	x	87

85	x	85

83	x	83

81	x	81

79	x	79

77	x	77

75	x	75

73	x	73

71	x	71

69	x	69

67	x	67

65	x	65

63	x	63

61	x	61

59	x	59

57	x	57

55	x	55

53	x	53

51	x	51

49	x	49

47	x	47

45	x	45

43	x	43

41	x	41

39	x	39

37	x	37

35	x	35

33	x	33

31	x	31

29	x	29

27	x	27

25	x	25

23	x	23

21	x	21

19	x	19

17	x	17

15	x	15

13	x	13

11	x	11

9	x	9

7	x	7

5	x	5

3	x	3

1	x	1



### Answer 4 :-

The values in kernels can be  initialized in differnt ways. 

Generally the initializiation can be a sample from  random distribution  or a sample from normal distribution with zero mean and standard deviation that is a function of the filter kernel dimensions. 

1. **initiliaze with 0**

 If we initializing all the weights with zeros then it leads the neurons to learn the same features during training.

2. **initiliaze with small or large numbers**

 However, initializing with too low or high numbers leads to vanishing or exploding gradients.


There are some advanced initailization techniques like **Xavier Initialiazation, He inititlaization** etc which are very popular and they are currently used by most of the frameworks like Keras, Tensorflow, Pytorch etc.

So we must always decide effective initialization methods.

We would like to test the diffrent initiliazation techniques when our model is not able to converge or when the training seems to be stuck for a long time before the loss function starts to decrease. 

### Answer 5 :- 

During the training of a Deep Neural Network the weights are initiliazed and then the forward propagation takes place.

Then the loss is calculated. **Loss** is defined as the difference between this predicted output and the actual output.

The value of the loss is then passed backwards through these filters and used to adjust the values in the filters to effectively minimize the difference between predicted and actual output. 

Then kernel values are updated via **backpropagation** while training.

This way the value of the filters are adjusted during training and the network will converge better and the loss will be minimized.
