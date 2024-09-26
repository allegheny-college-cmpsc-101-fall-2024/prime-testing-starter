# Primality Testing

TODO: Provide responses for the TODOs.

Make sure that all aspects of the `writing/reflection.md` correctly use all
of the features of the Markdown standard. This means that, when you preview your
Markdown it should always be formatted in a suitable fashion. For VS Code previews,
right click on the tab that shows the file name (e.g. `reflection.md`), then select
Open Preview.

Please make sure that you completely delete the TODO markers
from every line of the `writing/reflection.md` file.

Ensure that your writing is original and based on your own understanding
of the concepts.

TODO: Delete the phrase "Add Your Name Here" and then add your name.

## Add Your Name Here

## Program Output

### Use six fenced code blocks to provide output from different runs of `primality` with different inputs

#### Three outputs from running the exhaustive algorithm

TODO: Choose three different inputs to run the exhaustive search.
TODO: Ensure that at least one run produces meaningful profiler
output.

TODO: Provide the specific command that you ran to produce this output
TODO: Use a fenced code block to provide the output for this command.

TODO: Provide the specific command that you ran to produce this output
TODO: Use a fenced code block to provide the output for this command.

TODO: Provide the specific command that you ran to produce this output
TODO: Use a fenced code block to provide the output for this command.

#### Three outputs from running the efficient algorithm

TODO: Use the _same_ inputs as above to run the efficient algorithm
TODO: Ensure that at least one run produces meaningful profiler
output.

TODO: Provide the specific command that you ran to produce this output
TODO: Use a fenced code block to provide the output for this command.

TODO: Provide the specific command that you ran to produce this output
TODO: Use a fenced code block to provide the output for this command.

TODO: Provide the specific command that you ran to produce this output
TODO: Use a fenced code block to provide the output for this command.

## Performance Analysis

TODO: Compute the $ T_{\Delta} $ of running `primality` in efficient mode
instead of exhaustive mode. Use the equation in the project description
to explain how much faster one algorithm is compared to the other.

TODO: Make sure that you refer to the
[online description of this project](https://proactiveprogrammers.com/data-abstraction/engineering-efforts/primality-testing/)
to learn about computing percent changes in algorithmic efficiency.

TODO: Provide one paragraph that states which algorithm is fastest, by how much
it is faster, and how you knew that it was faster, referencing the data in
the aforementioned command outputs to support your response.

## Source Code

### Describe in detail how the completed source code works

#### A function that converts a `bool` into a human readable `str` value

TODO: Use a fenced code block to provide the requested source code
TODO: Write at least one paragraph to explain the requested source code

#### A function signature that defines the command-line interface for `primality`

TODO: Use a fenced code block to provide the requested source code
TODO: State how the CLI user access the parameters in the function signature.
TODO: Relate the accepted values of the CLI options to branches in the code.

## Professional Development

### How does the `pyinstrument` tool help you to evaluate the performance of a Python program?

TODO: Provide a one-paragraph response that answers this question in your own words.

### What was the greatest challenge that you faced when completing this assignment?

TODO: Provide a one-paragraph response that answers this question in your own words.

## Extensions

OPTIONAL: The extensions in this section have no impact on grade.
They are simply for further exploration if desired.

OPTIONAL: Gather data from 10 profiled runs of the exhaustive search,
and 10 profiled runs of the efficient search with the same input.
Compute the $ T_{\Delta} $ for each of the 10 runs, then take the grand
mean of the 10 $ T_{\Delta} $'s. Report both the grand mean, and the
standard deviation of 10 $ T_{\Delta} $'s.

OPTIONAL: Write a python script to do the empirical evaluation above
for 1, 10, 100, and 1000 runs. Include a plot showing the differences
in the grand means and/or the standard deviations.
