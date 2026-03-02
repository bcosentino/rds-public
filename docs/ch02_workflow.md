# Scientific workflow: Connecting ideas to data



The collection and analysis of data is a means to an end. I could devote the next year of my life to visiting city parks and recording the number of bird species that I see at each park, but who cares? In doing science, our goal is to use empirical data to derive understanding about how the world works. Understanding about what, exactly? That's up to you! Knowledge and understanding aren't gained from the data alone. The analysis and interpretation of data is only meaningful in light of a **research question**.

In science, a research question is a question about how the natural world works, and therefore a question that can be addressed with empirical data. In this chapter, I will describe different types of research questions one can ask and elements of what makes for a *good* research question. Then I will provide a high-level overview of how we will go about using data to provide insight into our questions. Together, the process of defining a research question and using data to address the question is what I will refer to as **scientific workflow**.

## Research questions

### Clarify your primary goal: description, prediction, or explanation?

A good research question clearly identifies the main task for using data. Do you want to describe some aspect of the world? Do you want to forecast a future event? Or, do you want to explain some phenomenon? Again, these are not necessarily mutually exclusive goals, but many research questions will fall into one of these buckets.

Consider the general topic of birds and city parks again. There are plenty of research questions one could ask about that study system. Table \@ref(tab:c02c01) provides a classification of research questions by primary goal, illustrating how different types of questions align with descriptions, predictions, and explanations.

\begin{table}[!h]
\centering\centering
\caption{(\#tab:c02c01)(\#tab:c02c01) Examples of description, prediction, and explanation questions.}
\centering
\resizebox{\ifdim\width>\linewidth\linewidth\else\width\fi}{!}{
\begin{tabular}[t]{lll}
\toprule
Description & Prediction & Explanation\\
\midrule
What is the average number of bird species in city parks? & How many bird species will be in a park with particular attributes, such as size, amount of forest, or number of visitors? & Does increasing the amount of forest in a park cause the number of bird species to increase?\\
How different are the types of bird species from park to park? & What will the total number of birds be in the park next year? & Does restricting visitor access increase the number of bird species?\\
\bottomrule
\end{tabular}}
\end{table}

### Identify the scope of inference: The who, what, when, and where of your study.

Let's take a look at one of the simple descriptive research questions from Table \@ref(tab:c02c01): What is the average number of bird species in city parks? Now, this isn't the most Earth-shattering research question, but it's simplicity will help make it clear why it's important to be specific about your question. The design of your research - how you go about collecting the data - should follow clearly from your research question. This requires you to clearly define the scope of inference for your question, namely who the question is about, what needs to be measured, when you need to measure it, and where you need to measure it.

The "who" and "what" parts of our research question are rather clear. We want to know about birds (who), and specifically, the mean number of city parks (what). But we need more. Where and when will we measure the mean number of bird species? We've answered the where question in part: city parks. But what city parks? Every city park in the world? City parks in Prague, Czech Republic? Moreover, when will you do the measuring? All we need to do is add some more detail on when and where. For example: What is the *current* mean number of bird species in city parks *within the boundary of Chicago, IL*?

Why do we need such specificity in our research questions? At the most basic level, specificity will help make it clear how to approach the process of collecting data. But at a broader level, the who, what, when, and where also defines the scope of inference of your research question. In statistics, the scope of inference is defined by the **population**. It's the entire group that we want to generalize about when asking a research question. In some cases, the population is rather small. For example, I might define the population as three particular city parks in Chicago: Union Park, Arrigo Park, and Eckhart Park. In other cases, the population will be very large, such as all the parks in Chicago.

Why does this matter? Defining the population, or the scope of your question, affects the types of generalizations you can make based on your research. Suppose I'm working on a research question involving causation, such as "What is the effect of screen time on cognitive performance?" In this case the hypothesis might be that the amount of time people spend on their phones, tablets, computers, and other devices affects there performance on cognitive tests. A study finding an effect of screen time on cognitive performance would be of great interest to the public. But what's the population for the study? If you address this question with a study on children, then you can't use the study to make generalizations about the effect of screen time on cognitive performance in adults. If you are interested in the effect of screen time on cognitive performance in adults, and you collect data from children, you're not really addressing the question.

So let's make this clear: When you state a research question, it is crucial to define the who, what, when, and where of your research question. These components don't necessarily need to be stated all at once in a single sentence. For example, it it's ok to frame your question as "What's the mean number of birds in Chicago city parks?", and then then clarify the timescale and the particular city parks you want to generalize about. Some of those details would be included in the Methods section of a paper on your study. Nonetheless, it's important to think about these questions as you start to articulate your research questions because it will help you design the methods of collecting data, and it will clarify the scope of inferences you can make based on your study.

I teach a statistics class as part of a biology curriculum. Most students who take my class are biology majors, but sometimes students from other majors that require statistics enroll in my course. In any given semester, I might ask: What proportion of the students in my class are biology majors? That’s a research question. It may not be a very interesting research question because it’s purely descriptive, but simple descriptions are often useful. For example, I could report the fraction of non-biology majors taking my statistics course to administrators who want to know how my department contributes to academic programs other than biology.

There are many examples like this. A company might first want to summarize the wages of their employees before considering a pay increase. A hospital might track the proportion of patients who return with post-surgical complications. A conservation biologist might calculate the average population size of a species in different habitat types.

In this chapter we'll look at some basic numerical and graphical quantities that can be used to describe data. But before we dig in, I want to distinguish between two scenarios with very difficult implications for how we should interpret *descriptive statistics*. Consider my question about the proportion of students in my statistics class majoring in biology. That question is very specific about *who* I want to make conclusions about. What proportion of the students in *my class* are biology majors? This is an example of a research question that is very limited in scope. In a typical semester, I have about 25 students in my statistics class. For my research question, those 25 students represent the **population** of interest.

The population defines the group from which data will be collected and inferences will be drawn. This is a critical concept because the population of interest defines the scope of inferences that can be made with data. All scientific studies involve making inferences with data, so it's critical that we define who we're making inferences about, and therefore who we *can't* make inferences about. For example, suppose I find that 60% of students in my class are biology majors. I can't use that observation to draw any conclusions about the proportion of biology majors in other statistics classes. Similarly, if a company wishes to describe the wages of its employees, the population is clearly its employees, and the data collected can't be used to describe wages at other companies.

### Make it interesting

Remember how science is a public process? The knowledge gained from science is not decided by any one individual. Thus, if you want your science to contribute to the advancement of knowledge, your science has to be of interest to others.

I'm not going to claim to be the final authority about what makes a question interesting; any given research question can be of interest to some and not to others. That said, I think interesting questions tend to have broader appeal to the public, addressing longstanding uncertainty or real-world problems (e.g., climate change, social equity). "What factors caused the evolution of *Homo sapiens* from our chimpanzee ancestors?" is an interesting question because many people want to know where human beings came from. "How does the SARS-CoV-2 virus infect people?" was an interesting question in 2019 because it had direct relevance for policy decisions about how to slow the COVID-19 pandemic.

Questions about causal explanation tend to be of greater interest than descriptive questions. Consider the causal questions in Table \@ref(tab:c02c01). Although they require some more detail on timescale and the population of interest, those questions could be of interest to others because they can inform public policy about urban design and biodiversity (and because a lot of people think birds are cool). If we know that adding forest will change the type of bird species present, then we might prioritize restoring forest to some parks to support certain species of birds.

Contrast the causal questions in Table \@ref(tab:c02c01) with this question: "How many bird species are in Union Park?". That's a valid research question, but it's purely descriptive and much more narrow in scope, and thus probably of less interest. Now, that's not to say descriptive research questions are never of interest! In 2018 the New York Times, the paper of record in the United States, "[published an article](https://www.nytimes.com/2018/10/06/nyregion/squirrels-central-park.html)" about a research team that was attempting to answer the question "How many squirrels are in Central Park?". That's a purely descriptive research question, but it happened to be about a species and a place that is of broad public appeal.

### Make it answerable with data

Remember that the confrontation of ideas with empirical data is really what distinguishes science from non-science. Thus, good *scientific* research questions are ones that can be addressed by collecting and analyzing data. My question about the amount of forest in urban parks and the types of birds can clearly be addressed by collecting data on forest cover and the types of birds present.

The challenge here is that even though a question might address a phenomenon in the natural world, there might not be an obvious type of empirical data that can settle the question. Questions about opinion are challenging for this reason. "What is the best style of pizza?" New York style? Chicago deep dish? Neapolitan? Detroit? This is an extremely important question! The problem is that there's not a definitive empirical definition of "best". Whereas I can clearly count bird species and ask where the number of bird species is maximized, I cannot clearly define what makes the "best pizza" because it is a matter of opinion. This is not to say that questions about opinion are off limits. "What style of pizza do people like the most?" is a question that we can address by collecting data on public opinion. Similarly, "What style of pizza is purchased the most in the world?" can clearly be addressed with data. Sometimes a question needs to be revised to make it more precise and tractable.

### Ground it in theory

Good research questions focused on explanation tend to follow logically from broader scientific theories. A scientific **theory** is a broad explanation about some aspect of the natural world. In other words, theories are explanations for *why* something happens the way it does. The theory of evolution is a well-substantiated set of ideas about how living things change over time. The theory or relativity is a well-substantiated set of ideas about space, time, and gravity. Good questions tend to fall under these broader theories, connecting a specific situation (the focus of your research question) to a more general idea about how the world works.

Consider the causal question in Table \@ref(tab:c02c01): "Does increasing the size of parks increase the number of bird species?". One relevant theory in ecology for this question is the theory of island biogeography. According to this theory, the number of species in patches of habitat should be determined by the balance of species immigrating to the patch and going extinct from the patch. The theory suggests that the size and proximity of habitat patches to other habitat play an important role in affecting immigration and extinction, and thus the number of species. In line with this theory, I might hypothesize that bird diversity in urban parks will be affected by the size of the parks and their proximity to other parks. A **hypothesis** is a specific statement about a particular system of interest that is grounded in a broader theory. In this case, the specific situation is about urban parks and birds, and my idea about urban parks and birds is grounded in island biogeography theory.

I can take this one step further and make a **prediction** about what I expect to observe in the data if my hypothesis is true. For example, I might predict that bird diversity is greatest in the biggest parks and parks that are the least isolated from other parks. If I don't find that pattern in the data, then I might want to revisit the broader theory. Maybe island biogeography theory is not sufficient, and I need to consider other broader ideas that could be applied to the specific case of urban parks and birds. Maybe it's not just the size of the habitat patch that matters, but also the types of vegetation in the patch, for example.

The key here is that your research question should have a logical connection to broader ideas in your discipline. Those broader ideas typically occur in a nested hierarchy. For example, the theory of island biogeography is part of the broader theory of biogeography, which consist of the set of ideas that help us explain the distribution of species on Earth. The logical connection between your research question and hypothesis to these broader ideas is critical to make your question coherent and relevant to other scientists.

### Make sure it's feasible

Good research questions are logistically feasible. Consider this extreme case: "What is the effect of removing humans from the Earth on biodiversity?" It's certainly an interesting question to ponder what biodiversity would look like if there were no humans, but this is not a feasible research study. Clearly it is not ethical to experimentally remove humans from the Earth, and even an observational design examining specific geographic areas where humans don't live would be challenging because human impacts on biodiversity occur across massive spatial scales (e.g., global climate change). Any comparison of areas with and without humans also carries the caveat that the places without humans don't really address the question, which is about how *removing* humans affects biodiversity.

Feasibility also matters at a smaller scale. For questions about urban parks and birds, I have to consider whether I can find enough urban parks that vary in the characteristics of interest to answer the question. Do I have the appropriate expertise to identify birds? Do I have access to the resources required to pull off the project (funding, equipment, time, etc.)? If my research question involves a temporal component, such as how urban park characteristics cause change in bird communities, will I be able to monitor bird populations for enough time to see a change, should one occur (potentially years, if not decades)? If I don't have the resources to do sampling on my own, is there an adequate dataset that's publicly available?

So good research questions are ones that are interesting, addressable with data, and grounded in theory, but also logistically feasible. This book will directly address how to design a study and analyze the data given a research question, and I suspect you will have a much better sense for the feasibility of particular research questions after exploring those issues.

### Avoid analyzing the data before stating your question

Sometimes researchers try to look for patterns in the data before clarifying their question and hypothesis. In the literature this has been called HARKing, or "hypothesizing after the results are known" ([Kerr 1998](https://journals.sagepub.com/doi/abs/10.1207/s15327957pspr0203_4)). The main problem with this research practice is that it increases the risk of making erroneous conclusions. As we will find out in coming chapters, sometimes patterns in the data occur simply by chance, in which case researchers will propose a causal hypothesis for a pattern that actually isn't real. Also remember that patterns in the data don't always reflect direct causal effects, as we saw with beta carotene and lung cancer risk.

So is it every OK to search for patterns in the data? Yes, absolutely. Consider this question: *"Why do some people recover more quickly from viral infections than others?"* The nature of this question is clearly causal. Indeed, the interest is in *explaining* why some people recover faster from viruses than others. Yet, no potential explanation has been proposed! This type of causal question is really a starting point. If there is little theoretical work on the question in the primary literature, then some initial exploratory analysis might be warranted, in which patterns of viral recovery among people are simply described. These questions are sometimes called "reverse causal questions" ([Gelman and Imbens 2013](https://www.nber.org/papers/w19614), [Bailey et al. 2024](https://www.nature.com/articles/s41562-024-01939-z)), in contrast to "forward causal questions" where a clear cause and effect are specified. Reverse causal questions can have an important place in science because identifying patterns can motivate or inform the development of more specific causal hypotheses.

The field of data science is very much focused on pattern recognition in the data, often for the goal of prediction. Consider this question: *"Does exercise predict a person's recovery time from viral infections?"* This question is clearly about prediction - "predict" is right in the question. Here the goal is to determine if the amount of exercise predict's a person's recovery. Maybe people who exercise more recover from viruses more rapidly. That doesn't mean exercise *causes* faster recovery, as exercise might be caused by some other factor that also affects viral recovery. Noncausal associations in the data can be very helpful for making accurate predictions, such as who is most likely to suffer from depression, who is most likely to earn a PhD, or whether the stock market is likely to tumble in the next five years. But it's critical to state up front that the goal in these causes is prediction and *not* causal explanations.

Consider this commonly used example. Suppose you want to predict how many people will go swimming at the beach. You scour through the data, and you find that one of the strongest predictors of whether people will swim is if they are wearing shorts. Great! You can collect data on shorts-wearing that will accurately predict the number of people swimming at your beach. But of course, wearing shorts doesn't cause swimming. Warm temperature is probably a common cause of shorts-wearing and swimming.

So it's really important to state your research question first, and to make it clear what your goal is. Causal questions in particular should be highly specific and grounded in theory. *"Does smoking slow a person's recovery time from viral respiratory infections"*. That's a very specific, forward causal question grounded in theory with a clearly identified cause (smoking) and effect (recovery time). If your questions are more about description or prediction, you simply need to be clear about that goal to avoid confusion.

::: {.alert .alert-block .alert-info}
<b>Explore More</b>

Huntington-Klein. The effect. Lipowski. E.E. 2008. Developing great research questions. Am J Health-Syst. Pharm.

Farrugia, P. et al. 2010. Research questions, hypotheses and objectives. Canadian Journal of Surgery.
:::

## Connecting ideas to data

Identifying a good research question is hard. What comes after the question isn’t much easier, but it is at least goal-driven: once you know what you want to learn, you can design a study and analysis that have a chance of answering it. In this section, I sketch an overview of **scientific workflow**, starting with a research question and showing how it guides decisions about study design, data collection, and data analysis. The goal here is not to provide a deep dive on components of the workflow, but rather to sketch the *big picture* of how to connect data to ideas. We will work through the details of each component of the reserach design and analysis steps in the remainder of the book. As an example for our big picture overview, we’ll use a question from the medical literature on diet and blood pressure:

> *Does a DASH diet lower systolic blood pressure compared to a typical diet?*

DASH stands for Dietary Approaches to Stop Hypertension and emphasizes fruits and vegetables. This topic has been studied extensively (e.g., Appel et al. 1997: <https://www.nejm.org/doi/full/10.1056/NEJM199704173361601>), but the design and data used are synthetic so we can focus on workflow rather than details of any one study.

The image below describes a high-level overview of scientific workflow showing how connections can be made between ideas and data. The figure is a simplified version of a workflow published by Deffner et al. (2024). The arrows illustrate logical connections between different components of a research project, linking elements that are largely “science side” (idea generation) and “statistics side” (data collection and analysis). The general idea is that theory should inform a research question and assumptions about causal relationships among variables relevant to the question (the **generative model**). Given a research question and causal assumptions, we can design a study and analysis, and then use the results to update our understanding of the system. The workflow emphasizes that science is iterative: conclusions from data can revise our beliefs and refine theory.

![](images/02_workflow.png)

Let’s walk through these components using our example question on the DASH diet and systolic blood pressure.

### Theory

**Theory** represents scientific knowledge that motivates the research question and informs the causal effects we think are plausible. There is a vast literature on cardiovascular disease and the risks of high blood pressure. Theory and prior evidence has suggested that diet should influence cardiovascular health via multiple physiological pathways, and more specifically, that that increasing fruit and vegetable intake (as emphasized in DASH) could reduce hypertension.

Theory also reminds us that diet is not the only factor expected to affect blood pressure. Age, exercise, smoking history, medication use, stress, and many other factors have been linked to hypertension. Indeed, most processes in the natural and social sciences are *multicausal*, meaning there's more than one cause of an outcome of interest. The challenge we face is that some factors create roadblocks to understanding the causal effects we actually care about. As just one example, consider the possibility that diet and exercise both influence blood pressure. That's not necessarily a problem, but it becomes a huge problem if diet and exercise are causally related to each other. For example, perhaps people vary in their degree of health consciousness, and people who are more health conscious tend to eat lots of fruits and vegetables and also exercise a lot. If we find a relationship between diet and blood pressure, is that because diet is having a causal effect on blood pressure, or is it actually an effect of exercise, and people who exercise a lot tend to have more healthy diets? In this example, health consciousness confounds the analysis, and we need to be aware of the issue so that we can use a research design or analysis to addresses the issue.

In this book we will use a variety of examples from across the sciences. I don't expect the reader to have deep knowledge of theory in those various fields, and I will do my best to provide sufficient theoretical background so that we can keep the focus on research design and analysis. But my point here is that effective research design and analysis requires knowledge of theory and prior research in your field.

### Research question

What is your question? This one is pretty straightforward:

> Does a DASH diet lower systolic blood pressure relative to a typical diet?

As discussed earlier in the chapter, a good research question is grounded in theory and has a clearly defined scope of inference (who, what, when, and where).

### Generative model

A **generative model** is a simplified story about how the data could be generated. In this book, we’ll express causal assumptions using **directed acyclic graphs (DAGs)**. DAGs are graphical models that represent variables as nodes and causal relationships as arrows. They include not only the causal effect(s) of interest (here the effect of diet on change in blood pressure), but also those other factors that could confound the analysis.

The structure of a DAG is informed by one's domain knowledge - the body of theory and prior research in your particular field. Recall that in real-world settings, we expect that people vary in health consciousness, and that health consciousness affects both diet and exercise. We can use a DAG to communicate those causal assumptions. Below is a simple DAG that includes the variables health consciousness, diet, exercise, and blood pressure.


``` r
dag_obs <- dagitty('
dag {
bb="0,0,1,1"

"Health consciousness" [pos="0.25,-0.5"]
Exercise              [pos="0.3,0"]
"Diet" [pos="0.2,0.0"]
"Change in systolic BP" [pos="0.25,0.50"]

"Health consciousness" -> Exercise
"Health consciousness" -> "Diet"
Exercise -> "Change in systolic BP"
"Diet" -> "Change in systolic BP"
}
')

ex <- edges(dag_obs)

# Highlight the confounding structure (backdoor paths into Diet and BP)
highlight_obs <- (ex$v == "Health consciousness" & ex$w == "Diet") |
                 (ex$v == "Health consciousness" & ex$w == "Exercise") |
                 (ex$v == "Exercise" & ex$w == "Change in systolic BP")

rethinking::drawdag(
  dag_obs,
  col_arrow = ifelse(highlight_obs, "firebrick", "black")
)
```

\begin{figure}

{\centering \includegraphics{ch02_workflow_files/figure-latex/c02c02-1} 

}

\caption{Observational setting: health consciousness confounds the relationship between diet and blood pressure change}(\#fig:c02c02)
\end{figure}

This DAG implies that a simple association between diet and blood pressure change could reflect not only the effect of diet, but also differences in health consciousness and exercise between people who eat different diets. This is the basic idea of **confounding**: other variables can create associations that complicate causal interpretation. The confounding pathway is highlighted in red in the DAG. One value of creating a DAG like this is that it tells the researcher and scientific community alike that the confounding effect of health consciousness must be controlled either as part of the study design or statistical analysis.

### Study design

Given a research question and generative model, we should then make decisions about how to collect data. In this book we will differentiate between two main types of study designs: **experiments** and **observational studies**. Essentially, experiments involve collecting data from individuals to which treatments (such as diet) have been randomly assigned. In contrast, observational studies involve collecting data from individuals in their natural settings without randomly assigning treatments.

Experiments are more powerful than observational studies for identifying causal effects because the process of randomizing treatments to individuals breaks up confounding between the treatment and other variables that affect the outcome of interest. Remember the generative model for the blood pressure example identified health consciousness as a confounding variable. People who eat more fruits and vegetables may be more health conscious and exercise a lot, and an association between diet and blood pressure may in part reflect the causal effect of exercise. But we're not interested in the effect of exercise for this study. We want to know the effect of *diet*.

Experiments offer a design solution. If we can *randomly* assign diets to individuals in an experiment, then we expect to have individuals of varying health consciousness (and thus exercise level) in each diet treatment. Randomization of diet to individuals blocks the arrow from health consciousness to diet in the DAG, such that any association between change in blood pressure and diet would be attributed to *diet*. If we used an observational design where we simply recorded diet and blood pressure among individuals in their natural settings - where people freely choose their diets and exercise levels - we would need to use statistical model that controls for the confounding effect of health consciousness.

We'll learn how to use statistical models with controls later in the book, but for now let's keep things simple and assume we use an experiment. Imagine we recruit 120 adults with elevated blood pressure, and we randomly assign 60 to a DASH diet and 60 to a typical diet. Each person maintains their diet for 8 weeks, and then we measure the change in systolic blood pressure from before to after the study. Pairing the measurements of blood pressure on each individual is a useful design approach because it helps control for other differences among individuals that could affect blood pressure.

### Estimand

To use data to answer a research question, we need to identify the **estimand**: the target quantity (or quantities) we want to learn about from the data that will address the research question. For our blood pressure study, we define the estimand as the difference in the average change in systolic blood pressure during the study between the DASH diet and the typical diet. Importantly, estimands are *not* the quantities computed from a particular sample. They are quantities we want to know about in the **population of interest**.

### Target population

Every research question needs a defined scope of inference called the **target population** (the who, what, when, and where discussed earlier in this chapter). For our blood pressure study, we might define the target population as adults with elevated blood pressure recruited from clinics in the United States during a defined time period. Target populations vary from study to study, but identifying the target population is essential because it determines who we can—and cannot—make claims about based on the study.

### Sample data

One of the fundamental problems of statistics is that we typically cannot measure every individual in the target population. Instead, we collect data from a **sample** of individuals drawn from the target population. For reasons we will discuss later, ideally we select individuals *randomly* from the population to be included in the sample. Because we observe only a subset of randomly-drawn individuals, the quantities we compute based on the sample data will vary from sample to sample. This is a major source of uncertainty in the quantities we estimate from sample data, and it's a topic we will address throughout the book.

Let's take a look at how the sample data might look for our study. Datasets are generally organized in tables with rows representing subjects and columns representing variables. Below are the first eight lines of a synthetic dataset, each having observations for five variables:

-   `id` = a unique ID code for each subject

-   `diet` = the type of diet randomly assigned to the individual

-   `sbp_pre` = systolic blood pressure measured at the beginning of the study

-   `sbp_post` = systolic blood pressure measured at the end of the study

-   `sbp_change` = difference in systolic blood pressure between the beginning and end of the study.

\begin{table}[!h]
\centering
\caption{(\#tab:c02c03)Toy dataset for the DASH example (synthetic values): one row per participant.}
\centering
\resizebox{\ifdim\width>\linewidth\linewidth\else\width\fi}{!}{
\begin{tabular}[t]{ccccc}
\toprule
id & diet & sbp.pre & sbp.post & sbp.change\\
\midrule
1 & DASH & 156.2 & 163.5 & 7.2\\
2 & DASH & 137.0 & 146.1 & 9.1\\
3 & DASH & 151.7 & 145.5 & -6.1\\
4 & DASH & 149.0 & 148.2 & -0.8\\
5 & DASH & 142.0 & 120.1 & -21.9\\
\addlinespace
6 & DASH & 119.8 & 115.6 & -4.2\\
7 & DASH & 141.2 & 128.8 & -12.4\\
8 & DASH & 137.8 & 128.4 & -9.3\\
9 & DASH & 151.4 & 147.8 & -3.6\\
10 & DASH & 144.3 & 144.6 & 0.3\\
\addlinespace
11 & DASH & 145.1 & 136.7 & -8.4\\
12 & DASH & 141.2 & 154.3 & 13.1\\
13 & DASH & 147.3 & 144.1 & -3.3\\
14 & DASH & 147.3 & 137.7 & -9.6\\
15 & DASH & 119.4 & 115.0 & -4.5\\
\addlinespace
16 & DASH & 166.2 & 157.4 & -8.8\\
17 & DASH & 157.4 & 140.6 & -16.7\\
18 & DASH & 152.6 & 148.6 & -4.0\\
19 & DASH & 140.3 & 139.9 & -0.4\\
20 & DASH & 158.3 & 153.3 & -4.9\\
\addlinespace
21 & DASH & 146.1 & 141.0 & -5.0\\
22 & DASH & 148.0 & 141.3 & -6.7\\
23 & DASH & 133.3 & 132.1 & -1.2\\
24 & DASH & 167.6 & 149.3 & -18.3\\
25 & DASH & 150.6 & 151.8 & 1.3\\
\addlinespace
26 & DASH & 172.9 & 157.6 & -15.3\\
27 & DASH & 170.8 & 165.5 & -5.3\\
28 & DASH & 150.7 & 148.9 & -1.8\\
29 & DASH & 157.7 & 151.6 & -6.1\\
30 & DASH & 170.7 & 150.2 & -20.5\\
\addlinespace
31 & DASH & 143.7 & 135.8 & -7.8\\
32 & DASH & 152.0 & 146.7 & -5.3\\
33 & DASH & 146.9 & 146.9 & -0.1\\
34 & DASH & 154.0 & 150.0 & -4.0\\
35 & DASH & 152.2 & 148.8 & -3.4\\
\addlinespace
36 & DASH & 164.0 & 165.1 & 1.1\\
37 & DASH & 157.1 & 143.5 & -13.7\\
38 & DASH & 139.3 & 126.4 & -12.9\\
39 & DASH & 156.9 & 148.9 & -8.1\\
40 & DASH & 140.1 & 134.8 & -5.3\\
\addlinespace
41 & DASH & 136.1 & 139.4 & 3.2\\
42 & DASH & 159.3 & 144.4 & -14.9\\
43 & DASH & 135.5 & 120.6 & -15.0\\
44 & DASH & 153.7 & 151.9 & -1.8\\
45 & DASH & 140.0 & 128.8 & -11.2\\
\addlinespace
46 & DASH & 167.0 & 157.3 & -9.7\\
47 & DASH & 158.5 & 155.4 & -3.2\\
48 & DASH & 145.2 & 132.3 & -12.9\\
49 & DASH & 159.6 & 145.8 & -13.8\\
50 & DASH & 155.1 & 145.1 & -10.1\\
\addlinespace
51 & DASH & 136.0 & 124.8 & -11.1\\
52 & DASH & 147.5 & 134.0 & -13.5\\
53 & DASH & 138.8 & 137.8 & -1.0\\
54 & DASH & 155.4 & 143.5 & -11.8\\
55 & DASH & 142.3 & 134.8 & -7.5\\
\addlinespace
56 & DASH & 147.2 & 140.3 & -6.9\\
57 & DASH & 135.2 & 112.3 & -22.9\\
58 & DASH & 138.5 & 133.2 & -5.2\\
59 & DASH & 151.6 & 155.6 & 4.0\\
60 & DASH & 138.0 & 129.9 & -8.1\\
\addlinespace
61 & Typical & 148.3 & 140.1 & -8.2\\
62 & Typical & 152.0 & 160.5 & 8.5\\
63 & Typical & 147.6 & 147.7 & 0.1\\
64 & Typical & 146.5 & 152.6 & 6.1\\
65 & Typical & 129.2 & 128.9 & -0.3\\
\addlinespace
66 & Typical & 146.7 & 149.6 & 2.9\\
67 & Typical & 128.4 & 138.0 & 9.6\\
68 & Typical & 163.8 & 167.1 & 3.3\\
69 & Typical & 138.0 & 139.0 & 1.0\\
70 & Typical & 151.8 & 144.4 & -7.4\\
\addlinespace
71 & Typical & 156.2 & 158.9 & 2.6\\
72 & Typical & 150.1 & 144.8 & -5.3\\
73 & Typical & 166.2 & 181.6 & 15.4\\
74 & Typical & 139.8 & 140.6 & 0.7\\
75 & Typical & 155.3 & 146.9 & -8.4\\
\addlinespace
76 & Typical & 138.3 & 149.4 & 11.1\\
77 & Typical & 175.5 & 169.8 & -5.7\\
78 & Typical & 158.3 & 143.6 & -14.7\\
79 & Typical & 145.9 & 135.5 & -10.4\\
80 & Typical & 159.4 & 157.8 & -1.7\\
\addlinespace
81 & Typical & 136.1 & 130.7 & -5.5\\
82 & Typical & 168.1 & 169.8 & 1.7\\
83 & Typical & 136.1 & 132.3 & -3.8\\
84 & Typical & 131.3 & 114.5 & -16.9\\
85 & Typical & 149.3 & 145.0 & -4.3\\
\addlinespace
86 & Typical & 160.2 & 172.3 & 12.1\\
87 & Typical & 149.9 & 144.3 & -5.5\\
88 & Typical & 140.9 & 134.2 & -6.7\\
89 & Typical & 164.1 & 161.1 & -3.0\\
90 & Typical & 179.0 & 190.2 & 11.2\\
\addlinespace
91 & Typical & 126.5 & 117.5 & -9.0\\
92 & Typical & 167.7 & 171.9 & 4.2\\
93 & Typical & 144.3 & 137.4 & -6.9\\
94 & Typical & 161.8 & 157.2 & -4.6\\
95 & Typical & 128.1 & 123.3 & -4.8\\
\addlinespace
96 & Typical & 146.9 & 151.1 & 4.2\\
97 & Typical & 138.5 & 141.4 & 2.9\\
98 & Typical & 144.1 & 150.7 & 6.6\\
99 & Typical & 137.1 & 143.6 & 6.5\\
100 & Typical & 154.4 & 169.7 & 15.3\\
\addlinespace
101 & Typical & 164.6 & 163.2 & -1.4\\
102 & Typical & 144.1 & 121.8 & -22.3\\
103 & Typical & 147.3 & 140.9 & -6.3\\
104 & Typical & 136.7 & 128.5 & -8.2\\
105 & Typical & 161.9 & 157.6 & -4.4\\
\addlinespace
106 & Typical & 156.7 & 164.0 & 7.2\\
107 & Typical & 131.2 & 124.7 & -6.6\\
108 & Typical & 167.8 & 159.3 & -8.4\\
109 & Typical & 136.0 & 137.9 & 1.9\\
110 & Typical & 137.4 & 141.0 & 3.6\\
\addlinespace
111 & Typical & 132.3 & 128.4 & -3.9\\
112 & Typical & 135.7 & 137.0 & 1.3\\
113 & Typical & 145.8 & 147.8 & 2.0\\
114 & Typical & 156.4 & 157.3 & 0.9\\
115 & Typical & 141.5 & 134.9 & -6.6\\
\addlinespace
116 & Typical & 147.6 & 151.5 & 3.9\\
117 & Typical & 146.6 & 126.5 & -20.1\\
118 & Typical & 164.1 & 167.0 & 2.9\\
119 & Typical & 177.5 & 178.7 & 1.2\\
120 & Typical & 137.2 & 151.6 & 14.4\\
\bottomrule
\end{tabular}}
\end{table}

### Statistical model

A **statistical model** is a mathematical description designed to connect the sample data to the estimand and measure uncertainty in the quantities we estimate. Below is an example statistical model that could be used for the blood pressure study. The first line of the model says that the change in blood pressure (*c*) for each individual *i* follows a normal probability distribution with mean $\mu_i$ and standard deviation $\sigma$. The second line says the expected mean blood pressure change for each individual *i* is defined by the mean for its diet treatment, $\alpha_{diet}$. The third and fourth lines mathematically represent our prior knowledge about the parameters in the model before looking at the data.

$$
\begin{array}{l}
c_i \sim \mathrm{Normal}(\mu_i, \sigma) \\
\mu_i = \alpha_{diet} \\ 
\alpha_{diet} \sim \mathrm{Normal}(0, 5) \\
\sigma \sim \mathrm{Exponential}(0.1)
\end{array}
$$

Don't worry about the details here. For now, the point is to show you that we'll need a mathematical tool to connect the data to the research idea, and that's the statistical model. Here the model allows us to estimate the mean change in blood pressure for each diet group, which can then be used to estimate the difference in blood pressure change between groups (the estimand). The model also allows for additional sources of variation in blood pressure change among individuals (represented by the standard deviation). These sources of variation could be any number of things, such as differences among individuals in medication, exercise, age, and so on. We don't need to enumerate all those sources of variation individually, but we do need a way to say - mathematically - that diet isn't the only source of variation in blood pressure change. We will build statistical models carefully later in the book.

### Estimate

An **estimate** is a numerical quantity computed from the sample data. For this study design, the estimate of the estimand is the the difference in the mean change in systolic blood pressure between the DASH and typical diet groups based on the sample data. The graph below shows the observed change in blood pressure for all 120 individuals in the study, separated by diet type. We can clearly see that individuals within each diet treatment vary in their blood pressure change, which is exactly what we expect because people vary in ways other than diet that might affect their blood pressure. But notice how the cloud of points tends to hover around 0 for the Typical diet, whereas individuals in the DASH treatment tend to have more of a reduction in blood pressure. In other words, it appears qualitatively that the *average* change in blood pressure during the study looks more substantial for the DASH diet than the typical diet.


``` r
ggplot(d_toy, aes(x = diet, y = sbp.change)) +
  geom_hline(yintercept = 0, linetype = "dashed") +
  geom_jitter(width = 0.12, height = 0, alpha = 0.5) +
  #geom_point(
  #  data = diet_summ,
  #  aes(x = diet, y = mu),
  #  inherit.aes = FALSE,
  #  size = 3
  #) +
  #geom_errorbar(
  #  data = diet_summ,
  #  aes(x = diet, ymin = lwr, ymax = upr),
  #  inherit.aes = FALSE,
  #  width = 0.15
  #) +
  labs(x = "Diet group", y = "Change in systolic blood pressure (mmHg)") +
  theme_minimal()
```



\begin{center}\includegraphics{ch02_workflow_files/figure-latex/c02c04-1} \end{center}



But we can't just rely on our eyes to detect patterns. We need to estimate the parameters in the statistical model, and specifically the estimand, the difference in blood pressure change between diets. We'll spend a great deal of time learning how to do this later in the book, for now I went ahead and fit the statistical model with the sample data so you can see the types of outputs you can expect. The graph below represents two outputs germain to the reserach question. In the left panel we see probability distributions for the average blood pressure change for each diet group. A probability distribution is just a technical term for saying some values of the mean blood pressure change are more likely than others. The figure suggests that the most likely values of blood pressure change are around -6.5 mmHg for the DASH diet, and -1 mmHg for the typical diet. The probability distributions emphasize that we can't be *certain* about the particular value of the mean blood pressure change in each group, but we can say - based on the data we collected - that some values are more likely than others. And it appears that the mean blood pressure decrease was more substantial in the DASH diet than the typical diet.



How substantial? We can estimate that too. Indeed, the difference in mean blood pressure change between diets is the estimand, so we definitely need to estimate the quantity. The panel on the right represents our estimate, being the probability distribution for the difference in mean blood pressure change between diets. Here we can see it's most likely that the DASH diet reduces systolic blood pressure by about 5-6 mmHg more than the typical diet. Importantly, we see it's extremely unlikely that the two diets have the same mean blood pressure change (represented by the value 0). Again, we can't be certain about the exact magnitude of the difference, but we can make probabilistic statements. Ultimately the inferences we make about our research question with data require *probabalistic reasoning*.

### Summary

Overall the synthetic study here suggests it's very *likely* that the DASH diet leads to greater reductions in systolic blood pressure than the typical diet. Thus we've come full circle. We started with a research question informed by theory, used a generative model to inform our research design and analysis, and fit a statistical model that allows us to make an inference about the research question in the target population of interest. Of course the science doesn't end there. This particular study has updated our knowledge on the effect of diet on blood pressure change, and it raises plenty of new questions that could be addressed next (e.g., What explains the variation in blood pressure change within the DASH diet? What are the physiological mechanisms underlying the blood pressure reduction with the DASH diet? How would variation in fruit and vegetable intake affect blood pressure reduction, and how much fruit and vegetable intake should be recommend to maximize blood pressure reduction?). In this way we see that science is an iterative process.

::: {.alert .alert-block .alert-info}
<b>Scientific workflow example</b>

-   **Research question:** Does a DASH diet lower systolic blood pressure compared to a typical diet?
-   **Theory:** Diet can plausibly influence blood pressure via physiological pathways.
-   **Generative model:** Factors like health consciousness can confound the relationship between diet and blood pressure and need to be considered in the study design and analysis to estimate the causal effect of diet.
-   **Estimand:** The difference in average systolic blood pressure change under DASH vs typical diet in the <i>target population</i>
-   **Target population:** The group we want to generalize about (e.g., adults with elevated blood pressure eligible for the study).
-   **Study design:** Randomized experiment assigning participants to DASH or typical diet and measuring systolic blood pressure before and after.
-   **Sample data:** The subset of individuals from the population selected for the study. One row per participant including diet group and blood pressure measurements.
-   **Statistical model:** A model that connects sample data to the estimand and allows us to describe uncertainty in our estimates.
-   **Estimate:** The difference in mean blood pressure change between diets based on the sample data and described with uncertainty.
:::

That's basically the whole ball game in one short chapter. The rest of the book will flesh out the details for each step of the workflow, building up a toolkit you can use to connect your own research questions to empirical data.
