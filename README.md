# Support Vector Machines: How Kernels and C Shape a Decision Boundary

A Support Vector Machine looks for the boundary that separates two classes with the **widest possible margin**. Two knobs decide how it behaves, and this notebook explores both visually: the **kernel** (what shape of boundary is allowed) and **C** (how strictly mistakes are punished).

## The experiment

Using the Iris flowers with only two features (petal length and width), the problem is turned into a binary one: *Virginica* against *everything else*. The notebook then trains SVMs with **polynomial kernels of different degrees** and **different values of C**, and plots every decision boundary side by side with its test score.

## The two knobs

- **Degree of the polynomial kernel.** Degree 1 gives a straight line. Higher degrees allow curved, more flexible boundaries that can capture non-linear structure, but too much flexibility makes the boundary wiggle around individual points.
- **C, the regularisation strength.** A small C accepts some misclassified points in exchange for a smooth, wide-margin boundary. A large C insists on classifying every training point correctly, which bends the boundary around outliers.

## What the results show

- **Degree:** boundaries stay smooth and scores stay good for degrees of about 3 to 5, with 4 the best compromise. Beyond that the boundary starts to oscillate and the score drops.
- **C:** test scores are above 90 % up to C ≈ 10, with the best result (around 95 %) at **C = 10**. The reasonable range is roughly C = 3 to 10. Around C = 15 and above the boundaries become sharp and convoluted, a visual sign of overfitting.

## What you can take from this

- Model complexity is a dial, not a switch. Plotting the boundary makes overfitting visible in a way a single score cannot.
- Kernel and C interact: a flexible kernel with a large C is the combination most likely to overfit.
- Evaluate on held-out data; the best hyperparameters are the ones that work on points the model did not train on.

## Files

- `SVM.ipynb`: the experiment, the boundary plots and the written analysis
