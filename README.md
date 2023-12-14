# Python Programming - Testing data for the Project 1 autograder

The `testing` folder contains all the datasets used by the autograder on Gradescope for Project 1. This is provided for you to re-test your functions, if it helps you better understand your results.

Except where otherwise indicated, the ballot data for each test can be found in the file called `taskX_ballots.txt`, where `X` is the corresponding test number.

Note that all submissions have been manually marked, and in particular where autograder tests have failed, this has been checked by markers, and corrected where autograder penalties were excessive.

Where possible, functions from previous questions were substituted for model solutions to test a later function; for example, in all functions where `tally_preferences()` was required, a model solution for `tally_preferences()` was used, to ensure that students were not penalised further if they had made a mistake with their `tally_preferences()` function.

## Expected results

### Task 1

| Test | `rank` | Expected result |
|--|--|--|
| 1.3a) | `1` | `[11, 1, 23, 25, 31, 9]` |
| | `5` | `[3, 5, 1, 0, 5, 0]` |
| 1.3b) | `1` | `[19, 31]` |
| | `2` | `[9, 10]` |
| 1.3c) | `3` | `[11, 24, 73, 34, 7, 58, 0, 113]` |
| | `7` | `[0, 3, 5, 0, 0, 1, 1, 0]` |


### Task 2

Note that results were checked to 4 decimal digits.

Common mistakes here include rounding results (sometimes to the nearest integer), and assuming that there would always be exactly 3 candidates/weights/possible ranks.

| Test | `weights` | Expected result |
|--|--|--|
| 2.2) | `[3, 2, 1]` | `[13, 17, 4]` |
| | `[0, 0, 1]` | `[1, 0, 2]` |
| | `[1, 1/2, 1/4]` | `[4.25, 5, 1]` |
| | `[1, 0.1, 0.01]` | `[4.01, 3.4, 0.12]` |
| 2.3a) | `[5, 4, 3, 2, 1, 0]` | `[176, 189, 220, 230, 247, 279]` |
| | `[1, 1/2, 1/3, 1/4, 1/5, 1/6]` | `[26.9, 29.25, 33.6, 33.56667, 41.6, 45.33333]` |
| | `[1, 0, 0, 1, 0, 0]` | `[18, 27, 20, 23, 37, 34]` |
| 2.3b) | `[2, 1]` | `[127, 1983]` |
| | `[1, 0.1]` | `[25.5, 985.5]` |
| | `[1, 0.2]` | `[35, 987]` |


### Task 3

The test data for Task 3 is all in the `task3_2*_ballots.txt` and `task3_2*_weight_sets.txt`. Expected results for each weight set are in `task3_2*_expected_results.txt`.

The autograder tests checked that the results were correctly calculated (using `positional_voting()` as required) and displayed, with a suitable figure size dynamically adapted depending on the number of required subplots. One test also checked that your `display_results()` function also worked in the case `N=1`, i.e. when only one chart was required.


### Task 4

Tests in Task 4 consisted of:

- 3 marks for correctness in no-tie cases
- 1 mark for efficiency in no-tie cases
- 3 marks for correctness in tie cases
- 1 mark for efficiency in tie cases

Efficiency tests worked by testing your function with increasingly large ballot arrays and a fixed timeout, so that tests fail if execution doesn't complete before the timeout. These were set up to run a full IRV election on these ballots array, and eliminating candidates one at a time, in reverse order of popularity. Note that final results were also checked for those tests, so your function could have been efficient enough but failed the test because it returned the incorrect result. Expected results are given in the table below.

Common mistakes include: incorrectly updating the `ballots` array or the `eliminated` list in-place; incorrectly handling the `eliminated` candidates; not dealing with the case where candidates are tied all the way down to the last possible rank; finding least popular candidates by index on an array with reduced number of columns (where, for example, 2 tied candidates always become "candidate 0" and "candidate 1" as their place in the original ballots is lost).

| Test | `eliminated` | Expected result |
|--|--|--|
| 4.3a) | `[1, 4, 6, 9]` | `8` |
| 4.3b) | `[1]` | `2` |
| 4.3c) | `[1, 3]` | `2` |
| 4.3d) | `[]` | `2` |
| | `[2]` | `1` |


| Test | Expected results (eliminated candidates, in order of elimination) |
|--|--|
| 4.4a) | `[6, 1, 2, 3, 4, 0, 5]`
| 4.4b) | `[2, 0, 3, 5, 11, 8, 10, 9, 1, 6, 4, 7]`
| 4.4c) | `[7, 10, 17, 1, 14, 9, 13, 8, 6, 5, 3, 16, 18, 15, 2, 0, 12, 19, 4, 11]`
| 4.4d) | `[26, 11, 25, 14, 8, 4, 18, 28, 16, 12, 29, 5, 22, 10, 19, 2, 24, 1, 23, 13, 15, 0, 6, 3, 20, 21, 27, 17, 9, 7]`


| Test | `eliminated` | Expected result |
|--|--|--|
| 4.5a) | `[0, 3]` | `4` |
| 4.5b) | `[]` | `3` |
| 4.5c) | `[1]` | `3` |
| 4.5d) | `[0, 2]` | `4` |
| 4.5e) | `[1, 3, 5]` | `7` |
| 4.5f) | `[]` | `1` |


| Test | Expected results (eliminated candidates, in order of elimination) |
|--|--|
| 4.6a) | `[6, 5, 3, 0, 4, 1, 2]`
| 4.6b) | `[9, 6, 8, 2, 0, 10, 7, 5, 3, 4, 1, 11]`
| 4.6c) | `[10, 18, 8, 6, 16, 0, 9, 2, 12, 4, 14, 1, 11, 5, 15, 3, 13, 7, 17]`
| 4.6d) | `[19, 28, 13, 7, 22, 11, 26, 3, 17, 0, 14, 2, 16, 12, 27, 4, 18, 6, 21, 5, 20, 8, 23, 10, 25, 1, 15, 9, 24]`


### Task 5

Tests checked that the resulting ballot array was as expected after eliminating multiple candidates, in the order given below. 3 marks were given for correctness. A further 3 marks were given for efficiency, using tests set up similarly as for Task 4.

The overwhelming majority of lost marks in this task were due to efficiency, particularly when students used loops over every single ballot instead of making use of more efficient indexing/slicing methods available with NumPy arrays.

| Test | Ballot data | `to_eliminate`, in order | Expected result |
|--|--|--|--|
| 5.2a) | `task5_2a_ballots.txt`| `4, 1, 6` | `task5_2a_results.txt` |
| 5.2b) | `task5_2b_ballots.txt`| `1, 6, 7, 4` | `task5_2b_results.txt` |
| 5.2c) | `task5_2c_ballots.txt`| `10, 2, 8, 7, 3, 4, 14, 12` | `task5_2c_results.txt3` |
| 5.3a) | `task4_6b_ballots.txt`| `6, 4, 9, 3, 1, 0` | `task5_3a_results.txt4` |
| 5.3b) | `task4_6c_ballots.txt`| `5, 17, 13, 2, 0, 6, 4, 16, 9` | `task5_3b_results.txt7` |
| 5.3c) | `task4_6d_ballots.txt`| `8, 0, 5, 28, 13, 11, 27, 25, 24, 7, 21, 22, 3, 18` | `task5_3c_results.txt1` |


### Task 6

Tests checked that the elected and eliminated candidates were returned correctly for a range of possible situations.

| Test | Expected `elected` | Expected `eliminated` |
|--|--|--|
| 6.2a) | `0` | `[2, 3, 1]` |
| 6.2b) | `1` | `[0, 2, 3, 4]` |
| 6.2c) | `4` | `[5, 13, 7, 12, 1, 3, 0, 8, 2, 9, 11, 6, 10]` |
| 6.2d) | `0` | `[]` |
| 6.2e) | `1` | `[0]` |


### Task 7

This was definitely the most difficult question! There are many different ways to implement STV correctly. Here is a broad summary of what was needed:

- Dealing with surplus transfer weights:
    - One way to do this is to keep track of a vector of transfer weights with the same length as the total number of ballots. When a ballot is transferred, it is now always transferred with a weight; in the case of an elimination, the weight is 1, but in the case of an election, the weight is calculated as per the surplus weight formula.
    - The weight applies to an entire ballot, and weights can be compounded by multiplying the new weight (upon a new transfer) by what the weight was previously.
- `update_ballots()` can then also be adapted to do this: update ballots exactly the same way as in Task 5, but also, in parallel, update the weight associated with each ballot.
- `tally_preferences()` can then be adapted to take weights into account: instead of counting the number of ballots for each candidate at a given rank, we can simply sum the weights of those ballots. For example, counting second preferences, if a candidate has 4 second-preference votes at weight 1 and 2 second-preference votes at weight 0.3, then the tally of their second-preference votes would be $4\times 1 + 2 \times 0.3 = 4.6$.
- Tie-break eliminations should be dealt with in the same way as in Task 4. `find_least_popular()` can be adapted to use the modified `tally_preferences()`. Both already-elected and already-eliminated candidates should be given to this function, as they should no longer be considered as possible least popular candidates.
- Tie-break elections should also be dealt with; again, `find_least_popular()` can be adapted to also be able to find the _most_ popular candidate if there are ties.
- Redistributing ballots when 2 candidates are elected at the same time is definitely the trickiest part, as no ballots should go to any other candidates which are elected simultaneously. This also means that 3rd preference votes which had these 2 candidates as first and second preference should also be redistributed, but only with the weight of the first-preference candidate. All of this can be dealt with inside the new `update_ballots()` function.

Tests were created with different properties, as seen on Gradescope. Students were able to achieve partial marks if they implemented some of the above correctly. Normally, students will also get at least +0.5 marks if they've made a genuine attempt at writing the function, even if all results are incorrect.

For this task, the best way to check your function is probably to check your first-preference tallies after each election and each elimination using the Glasgow dataset (`task7_glasgow.txt`), and comparing your results to [the intermediate results in the ballotbox.scot explainer](https://ballotbox.scot/councils/stv-explained/). The candidates are in the following order:

| Candidate number in the dataset | Candidate in explainer |
|--|--|
| 0 | UKIP |
| 1 | Lib Dem |
| 2 | MacLeod (SNP) |
| 3 | Conservative |
| 4 | Green |
| 5 | Raja (Lab) |
| 6 | Riaz (SNP) |
| 7 | Thomas (Lab) |


Here is the autograder test data if you'd like to try it:

| Test | `seats` | Expected `elected` | Expected `eliminated` |
|--|--|--|--|
| 7.3)  | `2` | `[3, 2]` | `[0, 1]` |
| 7.4)  | `2` | `[1, 2]` | `[0]` or `[0, 3]` |
| 7.5a) | `4` | `[0, 2, 3, 5]` | `[4, 1]` |
| 7.5b) | `3` | `[1, 4, 2]` | `[3, 0]` |
| 7.6)  | `3` | `[4, 0, 2]` | `[1, 3]` |
| 7.7)  | `2` | `[1, 5]` | `[3, 2, 0, 4]` |
| 7.8a) | `2` | `[0, 1]` | `[3, 4, 2, 5]` |
| 7.8b) | `4` | `[3, 1, 0, 5]` | `[4, 2]` |
