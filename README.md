# MATH-4470-Project
Final Project Outline: NHL Player Performance (EDA)

1. Introduction
Data: NHL skater stats (Rk, Player, Age, Team, Pos, GP, G, A, PTS, +/-, PIM, EVG, PPG, SHG, GWG, SOG, SPCT, TOI, ATOI, FOW/FOL/FO%, BLK, HIT, TAKE, GIVE). Cite Hockey-Reference as the source.
Why this data: Counting stats (goals, points, hits) are bounded below by 0, so they should be right-skewed. That makes the data a natural fit for reexpression and resistant methods.
Variables: Say which are categorical (Pos, Team) and which are numeric.

2. Questions
What does a typical player’s point total look like, and who are the outliers?
Do forwards and defensemen differ in scoring, and do the batches have unequal spreads?
How strongly are shots on goal related to goals? Which players score more or less than their shot volume predicts?
Does ice time (ATOI) predict points?
How does production change with age?
Do position and age group both shape production, and is the effect additive?
How well does a normal curve describe the distribution of ice time, and where does it fail?

4. Methods and Interpretation
Interpret each result in hockey terms. The EDA is a tool, not the story.

A. Single batch: PTS (Q1)
Stemplot (try 2 versions, with the “HI” line for McDavid-type outliers)
Letter values, midsummaries, five-number summary, fourth-spread
Fences and outliers
Mean vs. median, and a symmetry check with Hinkley’s d, a midsummary plot, and a symmetry plot
Reexpress with roots/logs and re-check symmetry. Handle zero-point players, e.g., use √(PTS + 0.5) as in the home-run example.
Bin ATOI (ice time) and make a rootogram with a resistant Gaussian fit, using mean = (F_U + F_L)/2 and s = (F_U − F_L)/1.349.
Make it a hanging rootogram and interpret the residuals in hockey terms (e.g., too few or too many players in certain ice-time ranges, reflecting how lineups are built).

B. Comparing batches: PTS by position (Q2)
Parallel boxplots, ordered by median
Spread vs. level plot, then use the slope (p = 1 − b) to pick a power
Re-draw the boxplots on the new scale and check that the spreads are more equal
Optional: compare matched medians (e.g., “centers are about X points higher than defensemen”)

C. Two-variable relationships (Q3, Q4)
Scatterplot of SOG vs. G, and ATOI vs. PTS
Check for curvature using the 3 summary points and the half-slope ratio, then straighten with a power transformation if needed
Fit a resistant line (rline) and compare it to least squares
Residual analysis:
Large positive residuals are over-performers, such as elite finishers.
Large negative residuals are under-performers, such as unlucky shooters or low-percentage shooters.
Check the residuals for patterns, e.g., by position.

D. Two-way table (Q5, Q6)
Build a table of median PTS (or PTS/GP) by position × age group (e.g., ≤22, 23–26, 27–30, 31+)
Median polish gives the common value, row effects, column effects, and residuals
Make an additive fit plot
If the residuals show the +/− quadrant pattern, try an extended fit (comparison values) or a log reexpression (multiplicative fit)

4. Conclusions
Answer each question in 2–3 sentences of plain language
Highlight the most surprising finding (an outlier, a skewness pattern, or a big residual)
Reflect on the “four R’s” (revelation, resistance, reexpression, residuals) and where each helped most

5. Limitations and Next Steps
One season only
Counting stats favor high-ice-time players
Possible next step: per-60-minute rates

6. Appendix
R code, the data dictionary, and the cleaning steps
