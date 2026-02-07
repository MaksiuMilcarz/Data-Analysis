# Task 3.4 - Final Recommendation on LMs in Education

Based on our analysis across Tasks 1, 2, and 3, here are our 4 key concerns:

---

1. **Models have "favorite letters" that fake their accuracy.** We found that Model X loves picking "A" and Model Y loves picking "D". When we dug deeper, Model X gets 97% of A-questions right - sounds great, but when it chooses A, it's only correct 37% of the time. It's basically spamming A whenever it's unsure. Model Y does the same with D. This means their accuracy scores are inflated by guessing patterns, not actual understanding. For education, this could mean students get unfairly graded depending on where the correct answer happens to be.

2. **Models fail when you shuffle the answers around.** If a model truly understands a question, moving the correct answer from position A to position C shouldn't matter. But it does - a lot. When we shuffled answer positions, all models performed worse. Model Z's stability score was roughly its accuracy squared (~43%), which is what you'd expect from random guessing. A tool we use to assess students should at least be consistent, and these models aren't.

3. **The raw data was a mess, and cleaning it introduced bias.** The models didn't just output clean A/B/C/D answers - they gave us stuff like "Answer: A", full explanations, "Not Sure", and other weird formats. After filtering and cleaning, Model Z lost way more data than X and Y. Some subjects had over 10% difference in how many questions each model actually answered. This kind of inconsistency makes it hard to trust these models in a real educational system where reliability matters.

4. **Cheaper models can't handle complex questions.** The government wants to save money with a faster "turbo" model, but it can only process 300 tokens. About 4.6% of questions are too long for it - and these tend to be the harder, more nuanced ones where we'd want the most accuracy. A hybrid approach could work (cheap model for simple stuff, expensive for complex), but it adds complexity. Also, the token "A" shows up way more often in text than B, C, or D (since "a" is just a common word), which might partly explain why Model X is biased toward A in the first place.

---

**Bottom line:** These models aren't ready to replace teachers or make decisions about students. They can help generate practice questions or give extra explanations, but for anything that actually matters, humans need to stay in the loop.
