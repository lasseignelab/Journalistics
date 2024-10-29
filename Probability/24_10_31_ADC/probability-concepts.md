# Probability Theory and Applications in Bioinformatics
##### Journalistics 10/31/24 Amanda D. Clark

## I. Fundamental Concepts

### A. Basic Definitions

1. **Experiment**: Action with uncertain outcome
   - DNA sequencing run
   - Random sampling of population
   - Protein structure prediction

2. **Random Variable**: Outcome measure; A variable whose value is determined by the outcome of an experiment
   - Number of mutations in a sequence
   - Expression levels
   - Quality scores in NGS

3. **Sample Space** (S): All possible outcomes of an experiment
   - All possible nucleotide sequences
   - All possible genotypes
   - All possible protein conformations

4. **Event**: Specific outcome or set outcomes of interest
   - Finding a particular mutation
   - Observing differential expression
   - Identifying a binding site
     
 **Event Space**: All possible ways an event can occur

### B. Types of Probability

1. **Joint Probability**: Written as Pr(A and B) or Pr(A ∩ B)
   - Probability of two events occurring together
   - Always ≤ min(Pr(A), Pr(B)) [Always less than or equal to the probability of either event alone]
   - Example: Pr(SNP and Disease)

2. **Conditional Probability**: Written as Pr(A|B) - read as "probability of A given B"
   - Probability of A given B has occurred
   - Can be larger or smaller than the original probability
   - Pr(A|B) = Pr(A and B)/Pr(B)
   - Example: Pr(Disease|SNP)

3. **Independence**
   - Pr(A|B) = Pr(A)
   - Pr(A and B) = Pr(A) × Pr(B)
   - Example: Independent assortment of genes

### C. General Examples

1. **Card Drawing Example**
   ```
   Drawing Ace of Spades (AS) as third card:
   - Direct: Pr(3rd is AS) = 1/50
   - Step by step:
     * Pr(1st is AS) = 1/52
     * Pr(1st not AS) = 51/52
     * Pr(2nd is AS | 1st not AS) = 1/51
     * Pr(2nd not AS | 1st not AS) = 50/51
     * Pr(3rd is AS | first two not AS) = 1/50
   ```

2. **Math Test Example**
   ```
   Given:
   - 25% passed both exams
   - 42% passed first exam
   
   Find: Pr(passed second | passed first)
   Solution: 
   - Pr(second|first) = Pr(both)/Pr(first)
   - = 0.25/0.42 ≈ 0.595 or 59.5%
   ```

3. **Medical Testing Example**
   ```
   Given:
   - Pr(Disease) = 0.01 (1% prevalence)
   - Pr(Positive|Disease) = 0.95 (95% sensitivity)
   - Pr(Positive|No Disease) = 0.10 (10% false positive)
   
   Find: Pr(Disease|Positive)
   Solution:
   Pr(Disease|Positive) = (0.95 × 0.01) / (0.95 × 0.01 + 0.10 × 0.99)
   ≈ 0.088 or 8.8%
   ```

4. **Dice and Coin Example**
   ```
   Rolling die and flipping coin:
   - Pr(H and 1) = 1/2 × 1/6 = 1/12
   - Pr(1 or 6) = 1/6 + 1/6 = 1/3
   - Pr(H and 1 or T and 6) = 1/12 + 1/12 = 1/6
   
   Sample Space: {H1,H2,H3,H4,H5,H6,T1,T2,T3,T4,T5,T6}
   ```

### D. Key Probability Patterns

1. **Joint to Conditional**
   ```
   Pr(A|B) = Pr(A and B)/Pr(B)
   Example:
   - Pr(passed both)/Pr(passed first) = 0.25/0.42
   ```

2. **Independent Events**
   ```
   Pr(A and B) = Pr(A) × Pr(B)
   Example:
   - Pr(heads and rolling 6) = 1/2 × 1/6
   ```

3. **Mutually Exclusive Events**
   ```
   Pr(A or B) = Pr(A) + Pr(B)
   Example:
   - Pr(rolling 1 or 6) = 1/6 + 1/6
   ```

4. **Updating Probabilities**
   ```
   Prior → Evidence → Posterior
   Example:
   - Disease probability before and after test
   ```

### E. Videos

[![Building Intuition](https://img.youtube.com/vi/4vmiaA3Qt4Y/0.jpg)](https://www.youtube.com/watch?v=4vmiaA3Qt4Y)


[![Jermaine Gordon](https://img.youtube.com/vi/cX-hAFH80Ls/0.jpg)](https://www.youtube.com/watch?v=cX-hAFH80Ls)



## II. Core Probability Rules

### A. Basic Operations
1. **AND Rule**
   - Independent: Pr(A and B) = Pr(A) × Pr(B)
     Example: Pr(heads AND six) = 1/2 × 1/6
   - General: Pr(A and B) = Pr(A) × Pr(B|A)
     Example: Pr(two aces) = 4/52 × 3/51

2. **OR Rule**
   - Mutually exclusive: Pr(A or B) = Pr(A) + Pr(B)
     Example: Pr(ace or king) = 4/52 + 4/52
   - General: Pr(A or B) = Pr(A) + Pr(B) - Pr(A and B)
     Example: Pr(heart or face card)

### B. Bayes' Theorem
1. **Formula**
   ```
   Pr(A|B) = Pr(B|A) × Pr(A) / Pr(B)
   ```

2. **Components**
   - Prior: Pr(A)
   - Likelihood: Pr(B|A)
   - Posterior: Pr(A|B)
   - Evidence: Pr(B)

### C. Videos

[![Emma Ding](https://img.youtube.com/vi/YexGjE7WWD4/0.jpg)](https://www.youtube.com/watch?v=YexGjE7WWD4)

[![StatQuest](https://img.youtube.com/vi/9wCnvr7Xw4E/0.jpg)](https://www.youtube.com/watch?v=9wCnvr7Xw4E)

## III. Bioinformatics Applications

### A. Sequence Analysis
1. **Position Weight Matrices**
   - Joint probabilities of bases
   - Conditional dependencies
   - Motif prediction

2. **Markov Models**
   ```
   Zero-order: Pr(base)
   First-order: Pr(base | previous base)
   Higher-order: Pr(base | previous n bases)
   ```

### B. NGS Analysis
1. **Quality Scores**
   ```
   Pr(error) = 10^(-Q/10)
   Q30 → Pr(error) = 0.001
   ```

2. **Variant Calling**
   ```
   Pr(Genotype|Reads) = Pr(Reads|Genotype) × Pr(Genotype) / Pr(Reads)
   ```

### C. Population Genetics
1. **Hardy-Weinberg Equilibrium**
   ```
   Pr(AA) = p²
   Pr(Aa) = 2pq
   Pr(aa) = q²
   ```

2. **Linkage Disequilibrium**
   ```
   D = Pr(AB) - Pr(A)Pr(B)
   ```

### D. RNA-Seq Analysis
1. **Differential Expression**
   ```
   Pr(DE|Data) = Pr(Data|DE) × Pr(DE) / Pr(Data)
   ```

2. **Count Models**
   - Negative binomial distribution
   - Poisson distribution

### E. Phylogenetics
1. **Substitution Models**
   ```
   JC69: Pr(A→G in time t) = 0.25(1 - e^(-4αt))
   ```

2. **Tree Likelihoods**
   - Joint probability of observed sequences
   - Conditional probability of evolution

## IV. Practical Considerations

### A. Statistical Testing
1. **Multiple Testing**
   - Bonferroni correction
   - False Discovery Rate (FDR)
   - Family-wise error rate (FWER)

2. **Power Analysis**
   - Sample size determination
   - Effect size calculation
   - Type I and II errors

### B. Model Selection
1. **Criteria**
   - AIC (Akaike Information Criterion)
   - BIC (Bayesian Information Criterion)
   - Cross-validation

2. **Validation**
   - Training/test splits
   - K-fold cross-validation
   - Bootstrap resampling

## V. Common Pitfalls and Solutions

1. **Base Rate Fallacy**
   - Solution: Always consider prior probabilities

2. **Independence Assumptions**
   - Solution: Test for correlations
   - Consider conditional independence

3. **Multiple Testing**
   - Solution: Apply appropriate corrections
   - Consider false discovery rates

4. **Model Overfitting**
   - Solution: Use cross-validation
   - Consider model complexity penalties

## VI. Best Practices

1. **Documentation**
   - Record all probability assumptions
   - Document model choices
   - Note parameter settings

2. **Validation**
   - Use multiple methods
   - Check assumptions
   - Perform sensitivity analysis

3. **Reporting**
   - Include uncertainty measures
   - Report all relevant probabilities
   - Provide confidence intervals
