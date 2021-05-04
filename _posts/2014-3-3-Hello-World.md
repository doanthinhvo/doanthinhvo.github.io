---
layout: post
title: Kmeans Algorithms
---
# 1. Objectives

What do I do in this blog

What can you gain after read it

1.1 Abstract

Introduce more about this object of blog. What it really be

# 2. Introduction

Introduce more about KMeans, and some problems related to that. Give some examples of what can KMeans do

# 3. Mathematical Analysis

### 3.1. Base

1. Vector

    write in form 
\matrix{1|⋯|⋮|⋰|1|⋯|1|⋮|1}  
2. Matrix/Np array

    Np array cơ bản là 1 list. Numpy list. Dùng numpy ở đây vì trong numpy có công thức tính kc vector có sẵn 

    Matrix A

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c614fb1c-7b5a-41eb-b3b8-416e02f1e5ca/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c614fb1c-7b5a-41eb-b3b8-416e02f1e5ca/Untitled.png)

3. Distance in space

### 3.3 Mathematics analysis

1. Input and output 

    Each vector was represented by *x,N,y,kx,N,y,k,...*

    Each matrix was represented by bold text (X,M,Y)

    KMeans algorithm take a set of observations **X**=[$x1,x2,x3,...,xN]$ belongs to R(dxN) where each observation is a d-dimension vector, N is the number of observations(members) and the number of groups(K, K<N) as two input. 

    The algorithm outputs the center of K groups [m1,m2,..mK] R(dxK) and the index of group that each member belongs to(label of group)

2. Lost function and Optimization Problems

    Let's yi=[yi1,yi2,yi3,...,yik] be the label of each observation xi. For example, if xi belongs to cluster 2, so yi2=1 and other yik will be equal to 0, and yi=[0,1,0,0,0...0]. That representation is called as one-hot.(very popular and widely use method)

    y1k={0,1}   and xichma(k=1 to K)(yik)=1 (1)

    Suppose xi(i<[1,N]) belongs to cluster k (k thuoc [1,K]), the lost value of observation xi is distance from xi to center mk in euclidean space. the lost value is (xi-mk). We'll find the way to this lost value min

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6643f043-e2d8-4e77-b6ca-f2bc204b9cde/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6643f043-e2d8-4e77-b6ca-f2bc204b9cde/Untitled.png)

    (2)

    Furthermore, because xi belongs to cluster k ⇒ yik=1. that leads to this equation

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be19d302-1a0a-496d-8229-dc06fa97ea68/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be19d302-1a0a-496d-8229-dc06fa97ea68/Untitled.png)

    This equation is the square error for 1 observation. The optimization goal is mininize square error of all observations in input set X(lost function), equation(4) where **Y**=[y1,y2,...,yN] be the matrix contain all label vector of N observations and **M**=[m1,m2,...mK] be the center of K groups

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc4d002a-08c8-4aac-b9df-36fc7d35aa8f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc4d002a-08c8-4aac-b9df-36fc7d35aa8f/Untitled.png)

    So, we need to optimization that

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/36f99a9b-2726-4e47-a263-aca9a86db509/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/36f99a9b-2726-4e47-a263-aca9a86db509/Untitled.png)

3. **Solving optimization problem**
    1. **Fixed M**, center of group 

        Because the M center is constant so the objective now is to correctly identify the label vector of each vector that each observation belonged to so that the square error in equation is minimized

        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/37c41696-b542-49a4-bb73-45a03b7b050b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/37c41696-b542-49a4-bb73-45a03b7b050b/Untitled.png)

        Because only one element of yi is 1. Equation (3) could be written as 

        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3933b4ea-8706-4af7-82be-78ae566c0613/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3933b4ea-8706-4af7-82be-78ae566c0613/Untitled.png)

        So the objective now is to find out that which cluster(j)(j thuoc [1,K] xi is nearest so that square error will be minimized

4. **Fixed Y**, label vector of each observation.

    after we find out the label vector of all observation, the optimization problem in equation (5) could be rewritten by the following equation.

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b77d06d7-5e0d-49ec-88bc-48affe1f9b59/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b77d06d7-5e0d-49ec-88bc-48affe1f9b59/Untitled.png)

    the right is a convex function. We can solve it by derivatives and find mj that make derivatives equal to zero.

    call l(mj)=yij(mj-xi)22

    derivatives that we have the following equation

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/39372b7a-0cc3-4d4c-8292-b13214504919/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/39372b7a-0cc3-4d4c-8292-b13214504919/Untitled.png)

    derivatives = 0 only when 

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/99812e40-6294-4c34-b13a-e8320434bc7c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/99812e40-6294-4c34-b13a-e8320434bc7c/Untitled.png)

    For each cluster j, the sum of i to N yij is to count how many observation in cluster j(if xi belong to j so yij=1 and if xi doesnt belong to j ⇒ yij=0) 

    tuong tu, voi mau so, with xi belong to cluster j ⇒ yij =1 and yij*xi=xi ⇒ tu so is the sum of all xi belongs to cluster j.

    we can say that new mj is the mean of all observation have assign to cluster j 

### 3.4 Discussion

1. Convergence
2. Initialization straegy

    One of the not available in that algorithm is we need to know the number of cluster. Not every time we can easy to see the relation of all observations. We can use the elbow method to fix that. I will introduce that in higher level

### 3.2 Application

1. Summary

    Step 1: Select K points as cluster centers randomly. (K is the number of groups/clusters)

    Step 2: Assign all data points to corresponding cluster center created in step 1 based on Euculidean distance.

    Step 3: Move cluster centers, the new centers are the means of coordination of data points among same group.

    Step 4: Repeat step 2 until convergence(when all cluster center remain unchanged after an interation)

    Step 5: Clustering process is done. Now when we have new data point, caculate distance between that data point to cluster center that we found and see what cluster that data belongs to

# 4. Application in Data Compression.

How can we do that 

Step

# 5. Conclusion

Summary your result

# 6. Acknowledgement

# 7. Source code and PDF report
\begin{equation} \tag{1}\label{eq:1} \sum_{k=1}^{K} y_{ik} = 1 \end{equation}
