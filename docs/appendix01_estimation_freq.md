\appendix

# Estimation with frequentist inference

Now that we have some basic principles of probability under our belt, we can turn our attention to the fundamental problem of inferential statistics: estimating parameter values from samples and characterizing uncertainty about our estimates. Having some basic understanding of probability was essential to explore the issues related to estimation, precisely because the language in which we will characterize uncertainty about parameter estimates *is* probability.



To keep things simple, we will explore the foundational principles of estimation in the context of the scientific problem we started to look at last chapter: estimating the prevalence of a disease in a population. We will use this example to develop the principles of estimation with different philosophies of inference, namely the frequentist and Bayesian approaches. Those terms should ring a bell from last chapter, as they represent the two different definitions of probability that we looked at.

Statistics education has been dominated by the frequentist approach. And there's good reason for that! Much of the scientific literature is dominated by the frequentist approach. In a way the situation has become a positive feedback loop. Frequentist methods are used by many (most?) professional scientists because those are the methods they are taught, and statistics instructors teach frequentist methods because those are the methods that are used. But Bayesian inference is being used more and more in the scientific literature, and for good reasons. Suffice to say that I think it's time to start teaching both approaches to inference. We'll start with the frequentist approach over the next two chapters, and then turn to Bayesian inference in the next chapter.

## Frequentist estimates are point estimates

Recall the scenario. We have a population of 10,000 people, and we need to estimate the prevalence of a disease to determine if public health interventions will be enforced. Those interventions will be enforced if the prevalence is 10% or greater. We still assume our test is perfect, but we don't have the time or resources to test all 10,000 people, so will randomly sample individuals for testing. We'll also assume that anyone who is randomly selected will comply with the test. I know, these aren't realistic assumptions, but it's useful to make simplifying assumptions to develop first principles.

OK, let's further assume that we randomly sample $N = 100$ people for testing. Out of the 100 tests, we find 8 positives and 92 negatives. Based on this single sample, we **estimate** the prevalence of the infection as

$$
\hat{p}_{infected}=\frac{8}{100}=0.08
$$

In other words, based on our sample we estimate that 8% of the population is infected. *Estimate* is a critical word here because we truly don't know what the actual prevalence of the infection is. We are trying to infer the true prevalence - that is, the parameter value - from a sample of data.

In frequentist inference, we try to draw conclusions about parameters in exactly this way. Frequentist inference assumes at the start that there is some true parameter value. We take a sample of data, and we estimate the parameter(s) of interest with the sample. Those parameter estimates are **point estimates**, in that they represent the single best estimate of the parameters of interest.

Because the frequentist approach assumes there is a single true parameter value, there's no way we can talk probabilisticaly about pramater values. For example, one might be tempted to ask "How probable is it that the prevalence of the infection is at least 10% given our sample of 8 of 100 infected?". In other words, we might want to know the conditional probability $P(p\geq0.1|\hat{p}=\frac{8}{100}=0.08)$. But from a frequentist perspective, this doesn't make sense. The true prevalence of the infection is either greater than 0.1 or not regardless of the data we observe in our sample. The parameter $p$ is completely fixed.

OK, but what are we supposed to make of our point estimate that 8% of the population is infected? Is it a good estimate or not? To interrogate the quality of an estimate with frequentist inference, we need to dig deeper and examine the concept of a sampling distribution.

## Sampling distributions

The key element of frequentist inference is that it considers an estimate from a single sample to be only one of many possible outcomes. Just imagine repeating the sampling process over and over again. Every new sample of 100 tests will produce varying point estimates becuase of samplign error. We estimated 8% of the population is infected based on our single sample, but if we were to take another random sample, maybe we'd find the estimate is 9%, or 6%, or 11%. In other words, frequentist estimates are random variables!

When we estimate a parameter with a random sample, is it possible that some estimates are more likely than others? Absolutely. Because the estimate is a random variable, it can be described by a probability distribution. In frequentist statistics, the probability distribution used to describe a sample estimate is called the **sampling distribution**.

Let's assume that the true prevalence of the disease is 11% in our population of 10,000 people. If that's the case, how likely is it that the estimated prevalence from a sample of 100 people will be 8%, as we saw in our sample? In probability terms, what is $P(\hat{p}=\frac{8}{100}=0.08|p=0.11)$. You might recognize that in this case, the estimated prevalence $P(\hat{p}$ is a binomial random variable, so we can quantify this probability with the binomial equation:

$$
P(X = 8) = \binom{100}{8} 0.11^8 (1 - 0.11)^{100 - 8}=0.088
$$

Of course we can quantify this easily in R:


``` r
dbinom(x = 8, size = 100, prob = 0.11)
```

```
## [1] 0.0880522
```

So we see that when we take a random sample of 100 people from a population with a true prevalence of 11%, the probability of our point estimate being 8% is 0.088. How does that compare to other possible values of the point estimate? Well, we can easily compute the probability of all possible outcomes for the number of positive tests and then plot the resulting distribution (Figure \@ref(fig:a01_chunk02)):


``` r
#all possible values of positive tests out of N = 100
x <- seq(from = 0, to = 100, by = 1)

#probability of each outcome assuming prevalence is 11%
p.hat <- dbinom(x = x, size = 100, prob = 0.11)

#combine into a data frame
d <- cbind.data.frame(x, p.hat)

#plot the sampling distribution
ggplot(d, aes(x = x, y = p.hat)) +
  geom_col(width = 1, fill = "steelblue", color = "black") + 
  labs(x = "Number of positives out of N = 100", y = "Probability") +
  xlim(0,30) +
  theme_classic()
```

<div class="figure" style="text-align: center">
<img src="appendix01_estimation_freq_files/figure-html/a01_chunk02-1.png" alt="Sampling distribution of the estimated prevalence of infection based on a sample of N = 100 individuals from a population where the true prevalence of the infection is 11%." width="70%" />
<p class="caption">(\#fig:a01_chunk02)Sampling distribution of the estimated prevalence of infection based on a sample of N = 100 individuals from a population where the true prevalence of the infection is 11%.</p>
</div>

The resulting probability distribution (Figure \@ref(fig:a01_chunk02)) shows the probability of each possible point estimate for the prevalence of the infection when we take a random sample of N = 100 from a population where the *true* prevalence is 8%. This is a *sampling distribution*! Sampling distributions show the probability distribution of all possible values for an *estimate* of a parameter when we take a random sample from the target population.

This is an extremely important concept. I have tried to make the case that the primary reason we need statistics is to guide decision-making about hypotheses in light of uncertainty. From a frequentist perspective, **the sampling distribution is an illustration of uncertainty about estimates taken from samples.** In this case, it shows us that when we take a random sample of 100 people, we won't necessarily find 11 positives (to give us an estimate of 11% prevalence) even if the true prevalence of the disease is 11%. It's certainly possible to get an estimate of 11% from a sample of N = 100, but it's almost just as likely to get an estimate of 10%, or 12%. Fundamentally these deviations in our estimates from the true parameter value are caused by random sampling error.

### Sampling distributions are centered on the true parameter value

One thing you should observe in the sampling distribution in Figure \@ref(fig:a01_chunk02) is that the distribution is centered on the true parameter value, 11%. That is a feature of sampling distributions. The expected value of a sampling distribution (the mean) *is* the true parameter value.

Now, you might be tempted to claim that our estimated prevalence of 8% is an inaccurate estimate. But that's not quite correct. When judging the accuracy of a parameter estimate from a frequentist perspective, you have to think about the distribution of possible estimates (the sampling distribution) rather than the single estimate you observed. Frequentist estimation is based on the idea of long-run frequencies of outcomes based on many random samples. In practice you only observe one, and because of sampling error, your one estimate is very likely to deviate from the truth. But accuracy of an estimator is judged on the expected value of the estimates, not the single estimate you observed.

This is where things get tricky for frequentist estimation. You have a single estimate in hand, but to judge the accuracy of that estimate, you have to think about the collection of possible, yet unobserved estimates that you would see if you repeated your sampling many times. It's an abstract idea! Our single estimate of 8% is indeed lower than the truth, but if you conducted sampling over and over again, you would see some estimates that are greater than the truth too. If estimates were consistently lower than the truth, then the estimates would indeed be biased.

I'm sure your wondering, "If I can't actually observe the sampling distribution, how do I know if my single estimate is accurate?". Good question! To judge the accuracy of your estimator, you really have to focus on aspects of the sampling design, namely the degree to which the observations you drew from the population were a random selection. Random sampling ensures that estimates - on average, across many samples - will be unbiased. In practice, there's nothing that we can quantify based on the concept of a sampling distribution that will tell us if your estimate is biased or not. To judge accuracy of estimates, you have to assess the sampling design, and especially assess whether the observations are a random sample.

### Sampling distributions allow us to estimate precision

Sampling distributions are abstract and can't tell us much about whether a single estimate is biased or not, but they can tell us a lot about the precision of our estimates. Indeed, the width of the sampling distribution is a measure of precision. In our example, we can see there's a reasonable chance of seeing anywhere from 5-16 positives out of 100 tests when the true prevalence is 11%. This variation is analogous to the variation in the number of heads you expect to see out of 10 flips of a fair coin. Although you expect 5 heads, you wouldn't be surprised to get 3, or 6, or 7 heads. In the same respect, we shouldn't be too surprised to see an estimated prevalence of 8% from a sample of N = 100 when the true prevalence is 11%. That variation is a feature of the sampling process, and it gets to the heart of uncertainty. When we sample from populations, there is random error in the outcome, and the width of the sampling distribution illustrates the uncertainty we should feel when we consider whether our sample estimate is any good. The wider the sampling distribution, the more uncertainty, and the less confidence we should feel about our estimate being close to the truth.

What factors affect the precision of estimates as represented by the width of the sampling distribution? Let's look at two: the sample size and variance.

#### Sample size affects precision

We previously identified sample size as one of the key drivers of precision. With the sampling distribution concept, we can interrogate that idea more precisely (pun intended!). We will continue assuming that the true prevalence of the disease is 11%, but we're not going to change the size of the sample that we draw from the population to estimate the prevalence. Let's construct sampling distributions where the sample size is 10, 100, or 1000 people:


``` r
#all possible values of positive tests
x10 <- seq(from = 0, to = 10, by = 1)
x100 <- seq(from = 0, to = 100, by = 1)
x1000 <- seq(from = 0, to = 1000, by = 1)

#probability of each outcome assuming prevalence is 11%
p.hat10 <- dbinom(x = x10, size = 10, prob = 0.11)
p.hat100 <- dbinom(x = x100, size = 100, prob = 0.11)
p.hat1000 <- dbinom(x = x1000, size = 1000, prob = 0.11)

#combine into a data frame
d10 <- cbind.data.frame(n = 10, p.hat = x10/10, prob = p.hat10)
d100 <- cbind.data.frame(n = 100, p.hat = x100/100, prob = p.hat100)
d1000 <- cbind.data.frame(n = 1000, p.hat = x1000/1000, prob = p.hat1000)
d_all <- rbind(d10, d100, d1000)
```

And now we can plot the sampling distributions:


``` r
#plot the sampling distribution
ggplot(d_all, aes(x = p.hat, y = prob)) +
  geom_col(data = d_all[d_all$n == 10, ], 
           fill = "steelblue", color = "black", width = 0.1) +
  geom_col(data = d_all[d_all$n == 100, ], 
           fill = "steelblue", color = "black", width = 0.01) +
  geom_col(data = d_all[d_all$n == 1000, ], 
           fill = "steelblue", color = "black", width = 0.001) +
  facet_wrap(~ n, ncol = 1, scales = "free",
             labeller = labeller(n = function(x) paste("N =", x)))+
  labs(
    x = "Estimated proportion of positives", 
    y = "Probability", 
  ) +
  theme_classic() + 
  theme(strip.background = element_rect(fill = "gray", color = "black"), 
        strip.text = element_text(color = "black", size = 11))
```

<div class="figure" style="text-align: center">
<img src="appendix01_estimation_freq_files/figure-html/a01_chunk04-1.png" alt="Sampling distributions of the estimated prevalence of infection based on samples of size N = 10, 100, and 1000 individuals from a population where the true prevalence of the infection is 11%." width="70%" />
<p class="caption">(\#fig:a01_chunk04)Sampling distributions of the estimated prevalence of infection based on samples of size N = 10, 100, and 1000 individuals from a population where the true prevalence of the infection is 11%.</p>
</div>

What do we notice about the sampling distributions under different sample sizes in Figure \@ref(fig:a01_chunk04)? First, each sampling distribution remains centered on the true parameter value of 11% prevalence. The point estimate of a parameter remains an unbiased estimate of the parameter no matter the sample size. In other words, sample size has no effect on the *accuracy* of estimates.

Second, as the sample size increases, the width of the sampling distribution decreases. We expect the estimated prevalence to change much more from sample to sample when the sample size is 10 than when it is 100 or 1000. Greater sample sizes lead to more precise estimates. This should make sense. After all, if you increase the sample size all the way to the size of the target population, there would be no variation at all in estimates from sample to sample.

The **Law of Large Numbers** states this explicitly, that as the sample size $N$ increases, the point estimate ultimately converges on the true parameter value. Let's simulate this process to get a good handle on it. Remember that we assumed a target population of 10,000 individuals. Below we will create a dataset of 10000 individuals with infection status classified as 1 (infected) or 0 (not infected), where 11% of the population is infected:


``` r
#create infection status for 10000 people with 11% infected 
status <- c(rep(1, 1100), rep(0, 8900))

#randomly order the observations 
set.seed(124)
status <- sample(status, replace=FALSE) 
head(status)
```

```
## [1] 0 1 0 0 0 0
```

``` r
#confirm the proportion infected is 11% 
mean(status)
```

```
## [1] 0.11
```

Now let's quantify the point estimate for the proportion infected as we increase the sample size from $N = 1$ to $N = 10000$. To get a sense for this, we can see above that the first individual is not infected (`status` = 0), so based on that individual with a sample size of $N = 1$, the estimated prevalence is 0%. Then we look at the second individual, who is infected (`status` = 1), making the point estimate $\hat{p}=\frac{1}{2}=0.5$ based on $N = 2$. The third individual is not infected, making the point estimate $\hat{p}=\frac{1}{3}=0.33$, and so on. We can compute the point estimate for each individual observation with the code below:


``` r
#creates the cumulative sum from each observation
status.cumsum <- cumsum(status)

#cumulative sample size 
n <- seq_along(status)

#quantify the point estimates
p.hat.infected <- status.cumsum/seq_along(status)

#create a dataframe
sim.law.large <- cbind.data.frame(status.cumsum, n, p.hat.infected)
head(sim.law.large)
```

```
##   status.cumsum n p.hat.infected
## 1             0 1      0.0000000
## 2             1 2      0.5000000
## 3             1 3      0.3333333
## 4             1 4      0.2500000
## 5             1 5      0.2000000
## 6             1 6      0.1666667
```

Now let's graph the estimated proportion against the sample size:


``` r
ggplot(sim.law.large, aes(x = n, y = p.hat.infected)) +
  geom_line(color = "steelblue", linewidth=0.7) +  # Line graph for p.hat.infected
  geom_hline(yintercept = 0.11, color = "red", linetype = "dashed") +  # Truth line
  labs(
    x = "Sample Size (n)", 
    y = "Estimated Proportion Infected", 
    title = ""
  ) +
  theme_classic() +
  theme(
    plot.title = element_text(hjust = 0.5)  # Center the title
  )
```

<div class="figure" style="text-align: center">
<img src="appendix01_estimation_freq_files/figure-html/a01_chunk07-1.png" alt="Illustration of the Law of Large numbers, showing that as the sample size approaches the size of the target population, the point estimate converges on the true parameter value." width="70%" />
<p class="caption">(\#fig:a01_chunk07)Illustration of the Law of Large numbers, showing that as the sample size approaches the size of the target population, the point estimate converges on the true parameter value.</p>
</div>

Figure \@ref(fig:a01_chunk07) illustrates the Law of Large numbers nicely. We see that the point estimate of the parameter moves around wildly when sample size is small, but eventually the sample size converges on the true value of 0.11. There are deviations between the point estimate and the true parameter value at basically every sample size below the size of the target population, but these deviations get smaller as the sample size increases. This phenomenon is true when trying to estimate any type of parameter, whether it is a proportion, mean, median, variance, etc.

#### Variance affects precision

Sample size is not the *only* factor that affects precision. Precision is also affected by the variance of the underlying random variable. Precision of a point estimate decreases as variance increases. This should make intuitive sense. The idea is that when there's greater variability in the underying distribution of the random variable, there's greater potential to select extreme observations into the sample, which increases the variability of the point estimate.

We can see this for our example of estimate disease prevalence. Remember that for the binomial distribution, the variance is determiend by the true proportion: $p(1-p)$ The variance reaches its maximum value when $p = 0.5$. Figure \@ref(fig:a01_chunk08) compares sampling distributions for when the prevalence is 11% vs. 50% with an identical sample size of N=100.


``` r
#all possible values of positive tests
x <- seq(from = 0, to = 100, by = 1)

#probability of each outcome assuming prevalence is 11%
p11 <- dbinom(x = x, size = 100, prob = 0.11)
p50 <- dbinom(x = x, size = 100, prob = 0.50)

#combine into a data frame
d11 <- cbind.data.frame(p = 11, p.hat = x/100, prob = p11)
d50 <- cbind.data.frame(p = 50, p.hat = x/100, prob = p50)
d_all <- rbind(d11, d50)

#plot the sampling distribution
ggplot(d_all, aes(x = p.hat, y = prob)) +
  geom_col(data = d_all[d_all$p == 11, ], 
           fill = "steelblue", color = "black", width = 0.01) +
  geom_col(data = d_all[d_all$p == 50, ], 
           fill = "steelblue", color = "black", width = 0.01) +
  facet_wrap(~ p, ncol = 1, scales = "free", 
             labeller = as_labeller(c(
            `11` = "p = 0.11, N = 100",
            `50` = "p = 0.50, N = 100"
        ))) +
  labs(
    x = "Estimated proportion of positives", 
    y = "Probability", 
  ) +
  theme_classic() + 
  theme(strip.background = element_rect(fill = "gray", color = "black"), 
        strip.text = element_text(color = "black", size = 11))
```

<div class="figure" style="text-align: center">
<img src="appendix01_estimation_freq_files/figure-html/a01_chunk08-1.png" alt="Sampling distributions of the estimated prevalence of infection based on a sample size of 100 when the prevalence of infection is 11% (low variance) vs. 50% (high variance)." width="70%" />
<p class="caption">(\#fig:a01_chunk08)Sampling distributions of the estimated prevalence of infection based on a sample size of 100 when the prevalence of infection is 11% (low variance) vs. 50% (high variance).</p>
</div>

Figure \@ref(fig:a01_chunk08) shows that the sampling distributions are centered in different locations, each being centered on the true parameter value (11% vs. 50%). But what you should also notice is that sampling distribution is wider (less precise) when the prevalence is 50% (higher variance) than when it is 11% (lower variance). The take-home here is that estimates will be less precise when sampling from random variables that have greater variance. Unlike sample size, this isn't something you can control.

This might make more sense with a different type of variable. Imagine that you're estimating the mean height of a group of people. We'll assume height follows a normal distribution where the true mean height is $\mu = 65$ inches. Let's further assume that we draw a sample of 100 people to estimate the height, but let's do so from two populations that differ in the variance of height. In one population, we'll assume the standard deviation is $\sigma = 5$ inches, and in the other population we'll assume the standard deviation is $sigma = 2$ inches. We can visualize these normal distributions and see that there's more variation among individual height when $\sigma = 5$ than when $\sigma = 2$ (Figure \@ref(fig:a01_chunk09))

<div class="figure" style="text-align: center">
<img src="appendix01_estimation_freq_files/figure-html/a01_chunk09-1.png" alt="Assumed distributions of height where the mean height is 65 inches and the standard deviation is either 2 or 5 inches." width="70%" />
<p class="caption">(\#fig:a01_chunk09)Assumed distributions of height where the mean height is 65 inches and the standard deviation is either 2 or 5 inches.</p>
</div>

We now go ahead and generate 10,000 replicate samples of N = 100 from the underlying populations, one where $\mu=65$ and $\sigma=2$ and the other where $\mu=65$ and $\sigma=5$.


``` r
set.seed(123)

#sample sizes to evaluate
stdevs <- c(2, 5) 

#empty data frame to store results
sampling_results <- data.frame()

#loop to simulate sampling process at each sample size 10000 times
for (stdev in stdevs) {
  
  #draw samples 10,000 times and compute sample mean
  sample_means <- replicate(10000, mean(rnorm(n = 100, mean = 65, sd = stdev)))
  
  #store results
  sampling_results <- rbind(sampling_results, 
                            data.frame(stdev = stdev, 
                                       sample_mean = sample_means))
}

#plot
ggplot(sampling_results, aes(x = sample_mean)) +
  geom_histogram(aes(y = after_stat(density)), bins=50, fill = "skyblue", color = "black", alpha = 0.7) +
  facet_wrap(~ stdev, nrow = 2, scales = "fixed",
               labeller = as_labeller(function(x) paste("SD =", x))) +
  theme_minimal() +
  labs(x = "Sample Mean Height (in)", y = "Probability density" ) +
  theme_classic() +
  theme(
    strip.background = element_rect(fill = "gray", color = "black"), 
    strip.text = element_text(size = 10, face = "bold"),
    plot.title = element_text(size = 16, face = "bold", hjust = 0.5)
  )
```

<div class="figure" style="text-align: center">
<img src="appendix01_estimation_freq_files/figure-html/a01_chunk10-1.png" alt="Sampling distributions of the estimated mean height from samples of N = 100 when the true mean is 65 inches but the standard deviations of height are either 2 vs. 5." width="70%" />
<p class="caption">(\#fig:a01_chunk10)Sampling distributions of the estimated mean height from samples of N = 100 when the true mean is 65 inches but the standard deviations of height are either 2 vs. 5.</p>
</div>

Figure \@ref(fig:a01_chunk10) shows that while both sampling distributions are centered on the true value of 65 inches (that is, the estimates are accurate), the sampling distribution generated from the population with $\sigma=5$ is much wider than the sampling distribution generated from the population with $\sigma=2$. In other words, precision is much lower when drawing samples from the population with greater variability of individual height, assuming equivalent sample sizes.

The take-home here is that precision will be greatest and uncertainty will be minimized when drawing large sample sizes from populations that have low variance. While you can control sample size as part of the study design, you can't control the underlying variance of the random variable being studied. Assuming equivalent sample size, estimates from distributions with more variation will more noisy than estimates from distributions with less variation.

### Sample size affects the shape of sampling distributions

Going back to the original comparison of sampling distributions at different sample sizes in Figure \@ref(fig:a01_chunk11), you might ahve noticed that the shape of the sampling distribution increasingly resembles a normal distribution as the sample size increases. This happens to be a consequence of the **Central Limit Theorem**, which states that the distribution of a sample estimates will be approximately normal at large sample sizes regardless of the shape of probability distribution for the underlying probability distribution.

Let me illustrate this last point with a different example, this time with a quantitative random variable. Suppose you were interested in estimating the average distance people live from an ice cream shop. We'll assume that the distribution of distances people live from an ice cream shop is skewed to the right. This means most people live close to an ice cream shop, and fewer and fewer people live far from an ice cream shop. This kind of random variable can be described by a **poisson distribution**, which is a probability distribution that often describes things we can count. Let's create a graph of the probability distribution assuming that the true mean distance to ice cream shop is 1 km:


``` r
#distances in kilometers
x <- seq(0, 10, by = 1)
prob <- dpois(x = x, lambda = 1) #lambda is the mean distance

#data frame for plotting
d <- cbind.data.frame(x, prob)

# Plot the probability distribution using ggplot2
ggplot(d, aes(x = x, y = prob)) +
  geom_bar(stat = "identity", fill = "skyblue", color = "black", alpha = 0.7) +
  labs(x = "Distance to ice cream shop (km)",
       y = "Probability") +
  theme_classic()
```

<div class="figure" style="text-align: center">
<img src="appendix01_estimation_freq_files/figure-html/a01_chunk11-1.png" alt="Probability distribution of distance to ice cream shop. Distance to ice cream shop was assumed to follow a poisson distribution with a mean of 1 km." width="70%" />
<p class="caption">(\#fig:a01_chunk11)Probability distribution of distance to ice cream shop. Distance to ice cream shop was assumed to follow a poisson distribution with a mean of 1 km.</p>
</div>

We can clearly see in Figure \@ref(fig:a01_chunk11) that the underlying distribution of distances is not normal! It's strongly skewed to the right and represents a poisson distribution. Now let's simualate the process of randomly sampling homes to estimate the mean distance people live from an ice cream shop.


``` r
set.seed(123)

#sample sizes to evaluate
sample_sizes <- c(1, 2, 5, 10, 50, 100, 500, 1000) 

#empty data frame to store results
sampling_results <- data.frame()
#loop to simulate sampling process at each sample size 10000 times
for (sample_size in sample_sizes) {
  
  #draw samples 10,000 times and compute sample mean
  sample_means <- replicate(10000, mean(rpois(sample_size, lambda = 1)))
  
  #store results
  sampling_results <- rbind(sampling_results, 
                            data.frame(sample_size = sample_size, 
                                       sample_mean = sample_means))
}

#plot
ggplot(sampling_results, aes(x = sample_mean)) +
  geom_histogram(aes(y = ..density..), bins = 30, fill = "skyblue", color = "black", alpha = 0.7) +
  facet_wrap(~ sample_size, nrow = 2, scales = "free",
               labeller = as_labeller(function(x) paste("N =", x))) +
  theme_minimal() +
  labs(x = "Sample Mean", y = "Probability density" ) +
  theme_classic() +
  theme(
    strip.background = element_rect(fill = "gray", color = "black"), 
    strip.text = element_text(size = 10, face = "bold"),
    plot.title = element_text(size = 16, face = "bold", hjust = 0.5),
    plot.caption = element_text(size = 10, hjust = 0.5)
  )
```

<div class="figure" style="text-align: center">
<img src="appendix01_estimation_freq_files/figure-html/a01_chunk12-1.png" alt="Sampling distribution for the estimated mean distance people live from an ice cream shop based on samples of size N = 1, 2, 5, 10, 50, 100, 500, and 1000. Note that the scale of the x-axis varies among plots (becoming more narrow as sample size increases) in order to highlight the shape of each sampling distribution." width="672" />
<p class="caption">(\#fig:a01_chunk12)Sampling distribution for the estimated mean distance people live from an ice cream shop based on samples of size N = 1, 2, 5, 10, 50, 100, 500, and 1000. Note that the scale of the x-axis varies among plots (becoming more narrow as sample size increases) in order to highlight the shape of each sampling distribution.</p>
</div>

Figure \@ref(fig:a01_chunk12) shows that as the sample size increases, the shape of the sampling distribution increasingly resembles a normal distribution. This happens even though the underlying probability distribution for the random variable is not normal. Indeed, we can see that when the sample size is only one, the sampling distribution is identical to the distribution of the underlying variable. But it doesn't take many observations for the sampling distribution to take on the classic bell shape of a normal distribution.

### Summary points on sampling distributions

That was a lot! But there's a reason for that. Understanding the concept of sampling distributions is really important for understanding how frequentist inference is carried out. Let's wrap up this section by summarizing some fundamental principles of frequentist inference related to sampling:

1.  If we take repeated samples from the same population to estimate a parameter, the estimates from different will not be the same due to random sampling error. The distribution of sample estimates given a specific sample size is the sampling distribution.

2.  The expected value of the sampling distribution is the true value of the parameter regardless of sample size. Because sample size doesn't affect statistical accuracy, the primary way to minimize bias in estimates is through research design strategies.

3.  As sample size increases, the precision of estimates increases, and the more likely a sample estimate will be close to the true parameter value. (Law of Large Numbers)

4.  The sampling distribution increasingly approximates a noral distribution as the sample size increases (Central Limit Theorem)

## Quantifying uncertainty: standard error and confidence intervals

Now that we know a) the width of the sampling distribution represents uncertainty about a parameter estimate and b) the sampling distribution is approximately normal under large sample sizes, we can turn to quantifying the degree of uncertainty in estimates from a sample. We'll quantify uncertainty in two ways, the standard error and confidence intervas.

### Standard error

Rather than just visually examining the width of a sampling distribution to gauge precision, we can quantify the variation in a sampling distribution. Recall that the standard deviation represents the variation among values for a random variable that follows a normal distribution. If the sampling distribution has a normal distribution, we can simply quantify the standard deviation of the sampling distribution as a measure of precision. The standard deviation of the sampling distribution is called the **standard error** and is quantified as the ratio of the standard deviation of the underlying random variable to the square root of the sample size:

$$
SE = \frac{SD}{\sqrt{N}} 
$$ 

This is a generic formula to quantify the standard error of an estimate taken from a sample when the sampling distribution is approximately normal. It can be applied to estimates of means, proportions, model coefficients, and more. The standard deviation is quantified differently for these parameters, so you will need to substitute $SD$ for the particular standard deviation formula for the parameter of interest. For example, the standard deviation of proportions is quantified as $\sqrt{p(1-p)}$, so the standard error of a proportion is:

$$
SE_{\hat{p}} = \frac{\sqrt{p(1-p)}}{\sqrt{N}}
$$ 

Consider our goal of estimating the prevalence of infection with a sample of 100 individuals when the true prevalence was 11%. Thus, the standard error is

$$
SE_{\hat{p}} = \frac{\sqrt{0.11(1-0.11)}}{\sqrt{100}} = 0.0312
$$

We know the estimate based on our single sample of N = 100 was 8%, which has a straightforward interpretation. But how do we interpret a standard error of 0.03? In a general sense, higher values for the standard error simply indicate more uncertainty (less precision) about the sample estimate. In other words, we should have more confidence in an estimate with a standard error of 0.03 than an estimate with a standard error of 0.1.

But maybe you have noticed there is a problem here. How can you compute the standard error of a sample estimate when you don't know the true population parameters? Look again at the formula for the standard error of the estimated prevalence. It includes the true prevalence as part of the formula for the standard deviation in the numerator. But we don't know the true prevalence! We're working through this process of estimation precisely because we don't know the true value of the parameter.

So what are we to do? In practice, the best we can do is substitute our estimate(s) for the true parameter value(s) in the formula for the standard deviation. You have to imagine the situation where we really don't know the true prevalence is 11%. All we know is that we've estimated the prevalence to be 8% based on N = 100. We use this information to estimate the standard error as

$$
SE_{\hat{p}} = \frac{\sqrt{\hat{p}(1-\hat{p})}}{\sqrt{N}} =\frac{\sqrt{0.08(1-0.08)}}{\sqrt{100}} = 0.0271
$$ 

You can see the estimated standard error is not that different from the true standard error [^ch08-1].

[^ch08-1]: It's a little awkward that the standard error estimate here is *lower* than the true value. This is actually a known bias under low sample size. Variances tend to be underestimated at low sample size, leading to lower estimates of the standard error at low sample sizes. There are different types of bias-correction factors that can be employed to adjust for this issue, but here we stick with the basic calculation of a standard deviation for a proportion for simplicity. 

### Confidence intervals

Recall the empirical rule, which states that for a normal distribution approximately two thirds of observations will be within one standard deviation of the mean, and approximately 95% of observations will be within two standard deviations of the mean. Thus, when we obtain a point estimate of a parameter from a sample and estimate the standard error (i.e., the standard deviation of the sampling distribution), we can use that information to quantify a *range* of possible values for the true population parameter at a given level of confidence. Such a range is called a **confidence interval**.

#### Quantifying confidence intervals when you know the standard deviation

Remember the standard normal distribution (*Z*)? The units of Z in the standard normal are in units of standard deviations. Let's find the value of Z that includes 95% of observations from the mean (which is 0 in a standard normal):


``` r
#what value of Z has 2.5% of observations below it?
qnorm(0.025, mean = 0, sd = 1, lower.tail=TRUE)
```

```
## [1] -1.959964
```

Here we see that 2.5% of observations are below the value Z = -1.96. Because the normal distribution is symmetric, this means that 2.5% of observations are also above the value Z = 1.96. Figure \@ref(fig:a01_chunk14) shows the standard normal distribution highlighting the middle 95% of observations.

<div class="figure" style="text-align: center">
<img src="appendix01_estimation_freq_files/figure-html/a01_chunk14-1.png" alt="Standard normal distribution showing hte middle 95% of observations between Z = -1.96 and Z = 1.96." width="672" />
<p class="caption">(\#fig:a01_chunk14)Standard normal distribution showing hte middle 95% of observations between Z = -1.96 and Z = 1.96.</p>
</div>

If we think about a standard normal distribution representing a sampling distribution, by definition there is a 95% chance that a point estimate of a parameter from a randomly drawn sample will be between Z = -1.96 standard errors below the true parameter value and 1.96 standard errors above the true parameter value. The Z score for our particular point estimate is

$$
Z = \frac{\hat{\mu}-\mu}{\sigma_\mu}
$$ 

where $\hat{\mu}$ is the estimated mean, $\mu$ is the true mean, and $\sigma_\mu$ is the true standard error. Thus, it must be the case that in 95% of random samples,

$$
-1.96 < \frac{\hat{\mu}-\mu}{\sigma_\mu} < 1.96
$$ 

Rearranging this inequality, we obtain a 95% confidence interval:

$$
\hat{\mu} -1.96*\sigma_\mu < \mu < \hat{\mu} +1.96*\sigma_\mu
$$

The inequality expresses the idea that we should be 95% confident that a point estimate $\hat{\mu}$ from a random sample will be within the range of values defined by $\hat{\mu}\pm 1.96*\sigma_\mu$. 

Can we apply this to our estimated proportion of infection?  Yes, we sure we can. Remember that under the central limit theorem, we expect sampling distributions to be approximately normally distributed under large sample size, and N = 100 is a reasonably large sample size. If our point estimate is 0.08 and the true standard error is 0.03, we can be 95% confident that the true parameter value is within the range $0.08\pm 1.96*0.03$, which corresponds to $0.021 < \mu < 0.139$. 

There's no reason we have to quantify confidence intervals at a level of 95%. Indeed we can quantify a confidence interval at any degree of confidence using the following general formula:

$$
\hat{\mu}\pm Z_{\alpha/2}*\sigma_\mu \\
$$ 
where $\alpha$ is the **significance value**. The significance value refers to the probability of observations in the tails, so the level of confidence is $1 - \alpha$. For example, $\alpha = 0.1$ for a 90% confidence interval. The quantity of $\pm Z_{\alpha}*\sigma_\mu$ is called the **margin of error**.

To quantify a 90% confidence interval for our example of infection prevalence, we simply need to find the value of Z leaving 10% of observations in the tails (5% of observations in each tail). Here's how we can do it in R:


``` r
#90% confidence level
alpha <- 0.1

#Z for 90% confidence level
z <- abs(qnorm(alpha/2, mean = 0, sd = 1, lower.tail=TRUE)) #abs for positive Z

#lower confidence limit: point estimate - z*SE
0.08 - z*0.03
```

```
## [1] 0.03065439
```

``` r
#upper confidence limit: point estimate + z*SE
0.08 + z*0.03
```

```
## [1] 0.1293456
```

We see that the 90% confidence interval for the point estimate 0.08 and standard error 0.03 is 3% - 13%. In other words, we can be 90% confident that the true proportion infected is between 3% and 13%. Notice that the range of confindence interval narrows as the confidence level decreases.

#### Quantifying confidence intervals when you don't know the standard deviation

Wait a second! The formula to quantify a confidence interval with the standard normal (Z) assumes that we know the standard deviation (and therefore the standard error) with certainty. We only know the true standard error in this case because we simulated the data, but again, we're estimating quantities precisely because we don't know them.

It turns out there's only a slight modification in our approach when we don't know the true standard deviation and standard error. But the approach differs when we're estimating proportions versus means. When we're estimating proportions with an unknown standard error, all we have to do is substitute the estimated standard error for the true standard error. In other words, a 95% confidence interval for a proportion is quantified as 

$$
\hat{p} -1.96*SE_{\hat{p}} < p < \hat{p} +1.96*SE_{\hat{p}}
$$

Thus, if all we had was our single sample with 8 out of 100 positive tests, the estimated standard error is 0.0271 (from above), and the 95% confidence interval can be quantified as is $0.08\pm 1.96*0.0271$, which corresponds to $0.027 < \mu < 0.133$. That's it! Really straightforward.

What about when we're estimating means? For means, things are slightly more complicated. The reason is that the normal distribution has two parameters, the mean and standard deviation, both of which must be estimated with data. In contrast, the standard deviation of a proportion is quantified directly from the value of the proportion itself. Ultimately this means there is slightly more uncertainty when estimating a standard deviation for normally distributed variables compared to binomially distributed variables. That additional uncertainty gets included as part of the process of quantifying the confidence interval.

How does it work? Rather than using the standard normal distribution, we use a normal probability distribution that has *slightly* heavier tails (i.e., slightly wider) compard to the standard normal distribution. This modified distribution is called a **t-distribution**. The degree to which more probability is added to the tails of a *t*-distribution relative to a standard normal is dependent on sample size. When the sample size is low, the standard deviation is being estimated with less precision, and more probability density is added to the tails to reflect greater uncertainty.

The particular shape of a *t* distribution is specified by the **degrees of freedom**, which in this case is defined as $df=N-1$. Thus, the appropriate *t*-distribution for a sample of size N = 50 has $df = 50 - 1 = 49$. As the sample size increases, the *t*-distribution converges on the standard normal distribution, which can be seen in Figure \@ref(fig:a01_chunk16).

<div class="figure" style="text-align: center">
<img src="appendix01_estimation_freq_files/figure-html/a01_chunk16-1.png" alt="Comparisong of t-distributions with varying degrees of freedom to the standard normal distribution (Z)" width="672" />
<p class="caption">(\#fig:a01_chunk16)Comparisong of t-distributions with varying degrees of freedom to the standard normal distribution (Z)</p>
</div>

Now that you have a sense for how the *t*-distribution compares to the standard normal, let's look at how confidence intervals are quantified with the *t*-distribution. 

$$
\hat{\mu}\pm t_{\alpha/2,df}*SE_\mu
$$ 

The formula is largely the same as before, except we've replaced the *Z* with a *t* distribution at a specified significance level *and* degrees of freedom ($t_{\alpha,df}$), and we've replaced the true standard error with our estimate of the standard error ($SE_\mu$). 

Let's work through an example. Suppose you're thinking about ice cream again, and you're interested in estimating the average weight of a single scoop of ice cream from your local ice cream parlor. You decide to go to the parlor on 10 randomly selected days and times, and you order a single scoop and weight it. The code chunk below creates a vector of the weights for 10 ice cream cones assuming a true normal distribution of weight with mean 113 g and standard deviation 15 g. A 95% confidence interval is then computed for the estimated weight:


``` r
set.seed(123)

#sample size
n <- 10

#ice cream weights (g) in sample of N = 10
ic <- rnorm(n = n, mean = 113, sd = 15)

#estimated mean
ic.mean <- mean(ic)
ic.mean
```

```
## [1] 114.1194
```

``` r
#estimated standard deviation
ic.sd <- sd(ic)

#estimated standard error
ic.se <- ic.sd/sqrt(n)
ic.se
```

```
## [1] 4.524195
```

``` r
#95% confidence level
alpha <- 0.05

#t for 95% confidence level and df = n-1
t <- abs(qt(alpha/2, df = n-1, lower.tail=TRUE)) #abs for positive t
t
```

```
## [1] 2.262157
```

``` r
#lower confidence limit: point estimate - t*SE
ic.mean - t*ic.se
```

```
## [1] 103.8849
```

``` r
#upper confidence limit: point estimate + t*SE
ic.mean + t*ic.se
```

```
## [1] 124.3538
```

We can see that the estimated (`p.hat`) mean weight is 113.02 g, the estimated standard error (`se`) is 3.66, the appropriate *t* value based on the degrees of freedom is 2.26, and the resulting confidence interval is 104.7 - 121.3 g. You should notice that the *t* value in this case, 2.26, is  greater than the *Z* of 1.96 for a 95% level of confidence. This reflects added uncertainty for estimating the standard deviation, and therefore the standard error, and ultimately results in a slightly wider confidence interval than compared to the interval based on a known standard error.

#### Interpreting confidence intervals

OK, back to prevalence of the infection. Based on our sample of N = 100 individuals, we estimated the prevalence was 8% with a 95% confidence interval of 2.7 - 13.3%. In other words, we can be 95% confident that true proportion infected is between 2.7% and 13.3%. I am purposely NOT saying that there's a 95% *probability* that the true proportion infected is between 2.7% and 13.3%.

Why can't we interpret our confidence interval in terms of probability? Well, this turns out to be one of the quirks of frequentist estimation. The frequentist definition of probability is about long-run frequencies! In order to determine confidence intervals probabilistically, you have to imagine have hundreds of thousands of confidence intervals from hundreds of thousands of random samples. If we have many 95% confidence intervals from many random samples, then we expect 95% of the confidence intervals to include the true population parameter. But any individual confidence interval? A frequentist would say that the true parmaeter is either in that single confidence interval, or it is not, so there is no probability to speak of for a single iteration.

We can simulate this situation to see exactly what I mean. We'll use the `rbinom` function to simulate 1000 random samples of N = 100 individuals when the probability of infection is 11%, then quantify a 95% confidence interval for each random sample, and finally quantify the proportion of confidence intervals that include 11%.


``` r
set.seed(124)

#10000 random samples of N = 100
sims <- 1000
alpha = 0.05
n <- 100
x.sims <- rbinom(n = sims, size = n, prob = 0.11)

lcl <- rep(NA, sims)
ucl <- rep(NA, sims)

for(i in 1:sims){
  x <- x.sims[i]
  p.hat <- x/n
  se <- sqrt(p.hat*(1-p.hat))/sqrt(n)
  z <- abs(qnorm(alpha/2, lower.tail=TRUE))
  lcl[i] <- p.hat - z*se
  ucl[i] <- p.hat + z*se
}

contains.truth <- lcl<=0.11 & ucl>=0.11
mean(contains.truth)
```

```
## [1] 0.939
```


``` r
#plot 20-randomly selected confidence intervals
set.seed(26) # Ensure reproducibility for sampling
indices <- sample(1:sims, 20)
ci.data <- data.frame(
  Interval = 1:20,  # Vertical positions
  LCL = lcl[indices],
  UCL = ucl[indices],
  ContainsTruth = contains.truth[indices]
)

ggplot(ci.data, aes(y = Interval, xmin = LCL, xmax = UCL, color = ContainsTruth)) +
  geom_errorbarh(height = 0.3, size = 1) +  # Plot horizontal confidence intervals
  geom_vline(xintercept = 0.11, linetype = "dashed", color = "black") +  # Add reference line
  scale_color_manual(values = c("TRUE" = "black", "FALSE" = "#E6AB02")) +  # Highlight intervals
  theme_classic() +
  labs(
    x = "Proportion Infected",
    y = "Randomly selected 95% CIs",
    color = "Contains true proportion (11%)"
  ) +
  theme(
    legend.position = "top",
    axis.text.y = element_blank(),  # Remove y-axis labels for clarity
    axis.ticks.y = element_blank()
  )
```

<div class="figure" style="text-align: center">
<img src="appendix01_estimation_freq_files/figure-html/a01_chunk19-1.png" alt="TODO: caption." width="672" />
<p class="caption">(\#fig:a01_chunk19)TODO: caption.</p>
</div>

Figure \@ref(fig:a01_chunk19) shows 20 randomly selected 95% confidence intervals for the proportion infected, highlighting confidence intervals that either do or do not include the true value of 11% infected. Note that of the 20 randomly-selected confidence intervals, 19 of 20 contain the truth, which is what we expect for a 95% confidence interval. If we look at the entire sample of 1000 random samples, 93.9% of them contained the true parameter of 11%. Why wasn't it exactly 95%? Well, there's sampling error even in our simulation process because we're not generating an infinite number of samples [^ch08-2].

[^ch08-2]: It turns out there's also a little bias due to the tendency to underestimate the standard deviation at low sample size. 

So the only time you should interpret frequentist confidence intervals probabilistically is when you have many confidence intervals. Which, of course, is almost never. We usually have a single point estimate and confidence interval based on a single sample. When that's the case, all we can do is say we are 95% confident (or whatever level of confidence is quantified) that the true parameter value is in the interval. This is a source of great frustration and misunderstanding, so if that's how you feel, you are in good company! You might even be asking yourself, what does it even mean to say we are"95% confident" about the true parameter being in a single interval? Good question. To me, it sort of sounds like a strength of belief, almost like a Bayesian interpretation of probability. Stay tuned. 

### The standard normal approximation does not work well under low sample size

The methods we've used in this section to quantify confidence intervals assume that the sampling distribution for an estimate follows an (approximately) normal distribution. This works well for continuous variables with underlying normal distributions, and it can even work well for random variables that don't have an underlying normal distribution. Indeed, we quantified a confidence interval for a categorical variable (proportion infected) assuming an approximately normal sampling distribution. As we now know from the central limit theorem this works well under reasonably large sample sizes.

So what is a large sample size? Well, there are some general rules of thumb. When estimating proportions for categorical variables, the central limit theorem application generally works when $np \geq 10$ and $n(1-p) \geq 10$. For example, in our example random sample where N = 100 and *p* = 0.11, these conditions are (barely) satisfied: $np = 100*0.11 = 11$ and $n(1-p) = 100*(1-0.11) = 89$. Of course, when you're estimating the proportion, you don't actually know the true proportion! In that case, you can use the estimated proportion to check if the rule of thumb holds. 

For our sample where we observed 8 out of 100 infected individuals, the rule would not hold:  $100*0.08 = 8$. What then? There are many alternative methods that have been applied for estimating confidence intervals for proportions under low sample size (or extreme values of the proportion near 0 or 1). For example, one approach to quantifying a 95% confidence interval for a proportion when $np < 10$  or $n(1-p) < 10$ is the Agresti-Coull Method. This method makes adjustments to the sample size ($n'=n+4$) and number of successes ($x'=x+2$) to compute an adjusted proportion ($p'=\frac{x'}{n'}$), which can then be used to quantify an adjusted standard error and confidence interval by replacing $p$ and $n$ with $p'$ and $n'$ in the formulas above. The `binom` package also has a function, `binom.confint` that can quantify an Agresti-Coull confidence interval directly by setting the `methods` argument to `ac`:


``` r
#agresti coull confidence interval
binom.confint(x = 8+2, n = 100+4, conf.level=0.95, methods="ac")
```

```
##          method  x   n       mean     lower     upper
## 1 agresti-coull 10 104 0.09615385 0.0513591 0.1697197
```

You can see in this case that the confidence interval is a adjusted a bit higher compared to the interval we quantified. 

