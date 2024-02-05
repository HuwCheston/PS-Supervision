# Section 4: Interpreting the Data

You should now have generated two clean quantitative data sets, each showing the amount of physical motion in a single musical performance at varying moments of intensity. We now need to carry out statistical analysis to see if there actually is any difference in the motion between the two videos.

## What is bootstrapping?

The bootstrap method is useful for estimating the distribution of a statistic (e.g. it's mean, variance) without assuming that it follows a normal distribution (as is required, e.g., for parametric methods like the t-test). The basic idea about how this method works can be found on [the Wikipedia page](https://en.wikipedia.org/wiki/Bootstrapping_(statistics)#Case_resampling). I'm reproducing the relevant passage below:

> First, we resample the data with replacement, and the size of the resample must be equal to the size of the original data set. Then the statistic of interest is computed from the resample from the first step. We repeat this routine many times to get a more precise estimate of the Bootstrap distribution of the statistic.

In more detail:
- Take a dataset, e.g. `[1, 2, 3, 4, 5]` (with `mean = 3`);
- Create a shuffled version of that dataset, where one value can appear in the new dataset several times, e.g. [`2,2,2,3,3`];
- Calculate the statistic of interest in the shuffled dataset, e.g. `mean = 2.4` for our dataset above;
- Repeat this process `N` times, so that we end up e.g. with an array of `N` means;
  - Usually the number of samples is pretty high, but it depends on what we're interested in doing with the distribution. For confidence intervals, I'd be skeptical of any analysis that doesn't calculate at least 10,000 samples.
- Considering the distribution of bootstrapped statistics, e.g. by calculating 95% confidence intervals by taking the 2.5 and 97.5 percentile.

## Calculate bootstrapped confidence intervals

:::{note}
If you're comfortable with R or Python, feel free to try bootstrapping your dataset using these languages. In Python, you'll probably want to investigate the [`df.sample`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sample.html) method in `pandas` (with `replace=True`), or the [`scipy.stats.bootstrap`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.bootstrap.html) function in SciPy. 
:::

Rather than having to go through the process of bootstrapping manually in Excel or Sheets (would be pretty painful), we can use the [online tool linked here](https://www.wessa.net/rwasp_bootstrapplot1.wasp) to help us.

In the `data` box, paste in the results of one of your scaled data columns. Set `# simulations` to at least 10,000, and `quantiles` to any value that includes `P2.5` and `P97.5`. You can then set the remaining values (mostly related to the output plots) to whatever you want. Finally, click `compute`, and you'll be taken to a new page after a few seconds of computation.

What we're interested on in the new page is the `mean` row in the `Estimation Results of Bootstrap` table. Make a note of the two values under the `P2.5` and `P97.5` columns; these are our 95% confidence intervals. Also, make sure that the computed mean (under the `Estimate` column) is the same as the actual mean of your data.

Repeat this stage with your second column of scaled data, and make a note of the estimated confidence interval for this column.

## Interpreting the results

Consider both confidence intervals. Do they cross? If so, we can consider the difference between mean motion in both videos not to be statistically significant: we can't be certain that the true means are not the same. If the confidence intervals don't cross, however, we can say that there is a statistically significant difference in mean motion between the two videos (although, see the below `Important` caveat)

:::{note}
If extracting a p-value is so important to us, one option is to consider the narrowest possible confidence intervals that cross. So, we can extend both confidence intervals to find the point at which they cross, taking the area outside the confidence interval as our estimate of p: e.g., if the confidence intervals crossed at `P2` and `P98`, we'd be able to say `p=0.04`.
:::

:::{important}

The above analysis should really come with a caveat. What we probably should have done is to shuffle both datasets, calculate the mean of each, compute the difference in means, and resample. This would give us a *single* distribution of mean differences, from which we could extract a confidence interval. If this confidence interval crossed 0, there would be no significant difference at `alpha=0.05`. We can also extend this to find a p-value as described above.

Unfortunately, there's no easy way to do this in Excel or Sheets, and no online calculator that can do it for us. But, if you're feeling adventurous, give it a go in Python or R!
:::

## Presenting your findings

Highlight both data columns and generate a line chart or histogram to demonstrate the differences in motion between the two. What differences do you notice between the high and low intensity videos? Is musical intensity significantly related to performer body motion? Why (or why not)?

**Try and think about these issues when answering the questions on the following page!**