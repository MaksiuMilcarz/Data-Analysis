# FIETS Poster Template
## Can AI Replace Teachers? A Critical Look at Language Models in Education

---

### Group 35: Bruna Cavalcanti Lauro, Igor Swierlikowski, Maksymilian Milcarz

---

## The Promise

The Dutch government's **FIETS** initiative explores using Language Models (LMs) to address teacher shortages and budget constraints in education. We evaluated three LMs (X, Y, Z) on the MMLU benchmark to determine if they're ready for the classroom.

[figure of a bicycle with AI/education icons - representing FIETS moving forward]

---

## Key Finding 1: Raw Performance is Misleading

**Initial accuracy scores looked promising...**

| Model | Accuracy |
|-------|----------|
| X     | ~77%     |
| Y     | ~75%     |
| Z     | ~66%     |

**But the data was messy!** LMs produced answers in 5+ different formats:
- Correct: `A`, `B`, `C`, `D`
- Verbose: `Answer: A`
- Explanatory: `The answer is A because...`
- Uncertain: `Not Sure`, `None of the above`

After cleaning, Model Z lost significantly more data than others, raising questions about reliability.

[figure of bar chart showing data loss per model after cleaning - X vs Y vs Z]

---

## Key Finding 2: Models Have "Favorite Letters"

**This is the most critical finding for education.**

Models don't actually understand questions - they have systematic biases toward certain answer positions:

| Model | Bias | Accuracy on Favored Letter | Precision When Choosing It |
|-------|------|---------------------------|---------------------------|
| X     | Loves "A" | 97% | Only 37%! |
| Y     | Loves "D" | 90% | Only 63% |
| Z     | No clear bias | ~65% | Balanced |

**What this means:** Model X gets most "A" questions right not because it understands them, but because it defaults to "A" when uncertain. When it chooses A, it's wrong 63% of the time!

[figure of bar chart comparing accuracy per answer letter (A, B, C, D) for each model - showing X's high A accuracy vs low D accuracy, Y's opposite pattern, Z's balanced pattern]

---

## Key Finding 3: Models Fail the "Shuffle Test"

If a model truly understands a question, shuffling the answer positions shouldn't matter. We tested this:

**Test-Retest Stability Results:**

| Model | Original Accuracy | After Shuffle |
|-------|------------------|---------------|
| X     | ~74%             | Much lower    |
| Y     | ~76%             | Much lower    |
| Z     | ~66%             | ~43% (approximately accuracy squared) |

**Interpretation:**
- Models X and Y lose accuracy when their "favorite" letter is no longer the correct answer
- Model Z appears to be essentially guessing randomly (stability = accuracy^2)

[figure of bar chart comparing original accuracy vs test-retest stability for all three models]

---

## Key Finding 4: Performance Depends on Dataset Design

The same models performed differently on two datasets:

| Model | MMLU Dataset | Other Dataset |
|-------|-------------|---------------|
| X     | 74%         | 79%          |
| Y     | 76%         | 72%          |
| Z     | 66%         | 67%          |

**Why?** The datasets have different answer distributions:
- MMLU: More balanced
- Other: More "A" answers (favoring Model X)

Chi-square test confirms: **Answer distributions are significantly different** (p < 0.001)

[figure of grouped bar chart showing answer key distribution (A, B, C, D) for MMLU vs Other datasets]

---

## Key Finding 5: Practical Trade-offs Exist

A cheaper, faster "turbo" model exists but can only process 300 tokens.

**Impact:** 641 questions (4.6%) exceed this limit

[figure of pie chart showing 95.4% questions fit vs 4.6% don't fit in 300 tokens]

**Affected subjects tend to be more complex** - exactly where we need the most reliability.

**Potential strategy:** Hybrid approach using cheap model for simple questions, expensive model for complex ones.

---

## The Token Perspective

LMs don't see text like humans - they see **tokens**.

The letter "A" appears in ~79% of all A/B/C/D token occurrences in questions and answers (because "a" is a common English word).

This may partially explain Model X's bias - it sees "A" tokens everywhere!

[figure showing tokenization example: "The answer is A" -> [token1, token2, token3, token4]]

---

## Conclusions & Recommendations

### What We Found:

1. **Performance metrics are deceptive** - High accuracy doesn't mean understanding
2. **Answer position bias is real** - Models have "favorite letters" that inflate scores
3. **Reliability is poor** - Models fail when tested on shuffled answers
4. **Context matters** - Performance varies based on dataset characteristics
5. **Trade-offs exist** - Cheaper models have practical limitations

### Implications for FIETS:

| Concern | Risk Level | Recommendation |
|---------|------------|----------------|
| Automated grading | HIGH | Models may systematically favor certain answer positions |
| Student assessment | HIGH | Results depend on how tests are constructed |
| Cost savings | MEDIUM | Hybrid approaches possible but add complexity |
| Reliability | HIGH | Human oversight remains essential |

---

## The Bottom Line

**LLMs are NOT ready to replace teachers.**

They can be useful as **assistive tools** for:
- Generating practice questions
- Providing supplementary explanations
- Supporting (not replacing) human evaluation

But for **high-stakes educational decisions**, human oversight is essential.

[figure of scale/balance showing "AI Assistance" on one side and "Human Judgment" on the other, with Human Judgment weighing more]

---

## Visual Summary

[figure of infographic showing the "journey" of findings:]
1. Data Cleaning -> Models produce messy outputs
2. Accuracy Analysis -> Performance looks good initially
3. Bias Discovery -> Models have letter preferences
4. Shuffle Test -> Models don't truly understand
5. Final Verdict -> Proceed with caution

---

## References

- MMLU Dataset: Hendrycks et al. (2020) "Measuring Massive Multitask Language Understanding"
- Test-retest stability methodology based on repeatability principles
- Data Analysis Clinic 1, KEN3450, Maastricht University

---

*This poster summarizes findings from the FIETS project evaluation conducted by Group 35.*

---

# Design Notes for Final Poster

## Suggested Layout (Single Page, Landscape):

```
+------------------------------------------------------------------+
|                     TITLE & GROUP INFO                            |
+------------------+-------------------+----------------------------+
|                  |                   |                            |
|  FINDING 1:      |  FINDING 2:       |  FINDING 3:                |
|  Data Quality    |  Answer Bias      |  Reliability               |
|  [bar chart]     |  [grouped bars]   |  [comparison bars]         |
|                  |                   |                            |
+------------------+-------------------+----------------------------+
|                  |                                                |
|  FINDING 4:      |  CONCLUSIONS & RECOMMENDATIONS                 |
|  Trade-offs      |  [bullet points with icons]                    |
|  [pie chart]     |                                                |
|                  |  BOTTOM LINE: Human oversight essential        |
+------------------+------------------------------------------------+
```

## Color Scheme Suggestions:
- Primary: Deep blue (trust, education)
- Accent: Orange/amber (caution, warning)
- Model X: Red
- Model Y: Blue
- Model Z: Green
- Background: Light gray or white

## Key Figures to Create:
1. Model accuracy comparison (before/after cleaning)
2. Answer position bias per model (A, B, C, D accuracy)
3. Test-retest stability comparison
4. Answer distribution per dataset
5. Token context limit pie chart
6. Final recommendation icons/summary

## Text Guidelines:
- Maximum 2-3 sentences per section
- Use bullet points
- Large, readable fonts
- Let the figures tell the story
