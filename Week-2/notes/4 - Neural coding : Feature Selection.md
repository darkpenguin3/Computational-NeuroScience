```
How to find the components of the model?

As discussed earlier, P(reponse | stimulus) and relating to watching-movie on how it's visualized through retina,
we face "dimensionality" problem especially with the frames generated in pixels.

So, we require to sample the responses of the system to stimuli.
As we sample, then they could characterize/feature the input details that triggers the responses.

P(response | stimulus) -> P(response | s1)
where s1 -> stimulus

```
```
Dimensionality reduction:
Let's start out with a very high dimensionaity description...
For example: an image or a time-varying waveform.
On taking the example, just pick out a small set of relevant dimensions.
```
```
Let s be the stimulus and the plot points be s1, s2,...
Let t be the time and the plot points be t1, t2,...
```
![](http://geekresearchlab.net/coursera/neuro/neural-feature-1.jpg)
<br>
```
Question:
If we discretize a stimulus waveform in time, 
we can represent it as a vector in some vector space. 
What is the dimensionality of this vector space?
Answer:
The number of points used in the discretization.
Explanation:
When we represent a discretized stimulus as a vector, the first axis corresponds to the value of the stimulus at the first time point, the second axis to the value of the stimulus at the second time point, and so on. 
Thus, the dimensionality of the vector space (and all the vectors within it) is the number of time points used to discretize the stimulus. Note that we often label the axes by their corresponding times, even though the elements of the stimulus vector have the same units as the y-axis of the original stimulus waveform.
```
```
Determining the right stimulus to use:-
As sampling the reponses over variety of stimuli upon featuring the input that triggers,
P(reponse | stimulus) -> P(response | s1,s2,s3... sn)
The cool useful method that can be used is "Gaussian white noise".
```
![](http://geekresearchlab.net/coursera/neuro/neural-feature-2.jpg)
<br>
```
Question:
When we represent Gaussian distributions using the classic bell-curve shape, 
what do the axes represent?
Answer:
The x-axis is the stimulus parameter and the y-axis is the probability (density) of the stimulus parameter.
Explanation:
When we plot a one-dimensional distribution the x-axis represents some stimulus parameter (such as the projection of the stimulus onto a feature), and the y-axis represents the probability density of sampling a stimulus with that parameter value from the distribution. 
If we were interested in the probability density over two features, we would let the x- and y-axes be the projections of the stimulus onto those two different features and the z-axis be the probability.
```
![](http://geekresearchlab.net/coursera/neuro/neural-feature-3.jpg)<br><br>
![](http://geekresearchlab.net/coursera/neuro/neural-feature-4.jpg)<br><br>
![](http://geekresearchlab.net/coursera/neuro/neural-feature-5.jpg)<br><br>
![](http://geekresearchlab.net/coursera/neuro/neural-feature-6.jpg)<br>
```
Now, We have found how to find the components of this model?
The components of the model can be found by using,
(i) Gaussian White Noise and (ii) Spike Trigggered Average (STA)
```
<br><br>
![](http://geekresearchlab.net/coursera/neuro/neural-feature-7.jpg)
<br>
```
Now, the next question is: "How do we find the input/output of the system" with respect to the feature?
```
![](http://geekresearchlab.net/coursera/neuro/neural-feature-8.jpg)
<br>
```
Question:
When we plot P(spike | s1) as a function of s1, why does P(spike) only act as a scaling factor, rather than as something that changes the general shape of the function?
Answer:
P(spike) is not a function of s1.
Explanation:
P(spike) is the prior probability of observing a spike. 
This is calculated independent of the stimulus.
```
![](http://geekresearchlab.net/coursera/neuro/neural-feature-9.jpg)<br><br>
![](http://geekresearchlab.net/coursera/neuro/neural-feature-10.jpg)<br><br>
![](http://geekresearchlab.net/coursera/neuro/neural-feature-11.jpg)<br>

```
Principal Component Analysis (PCA): 
```
![](http://geekresearchlab.net/coursera/neuro/neural-feature-12.jpg)
<br>
```
Let x, y, z be the axis and plots being plotted in three dimensional space.
Actually, the data lies in the two-dimensional plane.
If we run PCA, then we'll find two principal components.
And these components correspond to the set of vectors that expand the two-dimensional space.

But, what if we had 100 dimensions? We can't be plotting the coordinates one against the other.

For those of you having linear algebra background, PCA gives a basis for the datasets that represents the data,
where it uses a lot smaller than the original representation.
Hence, we get compression and it's also well-matched dataset to that particular dataset.
```
![](http://geekresearchlab.net/coursera/neuro/neural-feature-13.jpg)<br><br>
![](http://geekresearchlab.net/coursera/neuro/neural-feature-14.jpg)<br>
```
Question:
Principal component analysis (PCA) gives us a method to ?
Answers:
(i) Find a representation of our data which has lower dimensionality, giving us a computationally easier problem to work with.
(ii) Find the vectors along which the variation of our data is maximal in our feature space.
Explanation:
The spike-triggered average gives us a simple view of the stimuli that lead up to a spike, but because of its simplicity it cannot capture some of the interesting dynamics that can occur. 
In this case, if a cell responds to both positive/negative changes and negative/positive changes, the spike-triggering stimuli will average to zero, making the spike-triggered average look like a flat line. 
That does not give us much useful description! 
Principal component analysis can help is pull out the right number of dimensions we need to describe the stimulus features the neuron is looking for.
```
![](http://geekresearchlab.net/coursera/neuro/neural-feature-15.jpg)
