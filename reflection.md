## 1 : In round 2 it said that no handoff file existed because round one never had a handoff to go off of, it was just using the requirments written by me

## 2 : In round 4 it had a problem with changing R6 because the old tests hadnt been changed to work with the alternated units of measurment. It was important to chage this because not all lifters use lbs as their unit of measurments, and convernting from lbs to kg by hand is not efficient for time.

## 3 : The test `test_R6_same_mass_in_other_unit_is_not_improvement` in `lift-log/tests/test_round4.py` lines 152-162 checks that when you put the same wieght in two different measurments units doesnt count it as an improvement in strength 
 def test_R6_same_mass_in_other_unit_is_not_improvement(data_file):
        """R6/R9: 68.0388555 kg then 150 lbs is the same mass, so no gain.
        ...
        """
        log(data_file, weight="68.0388555", unit="kg", date="2026-11-01")
        log(data_file, weight="150", unit="lbs", date="2026-11-08")
        assert run(data_file, "improved").stdout.strip() == \
            "No improvement recorded yet."

## 4 : My commit 9f088fc Add prs command showing each exercise's personal record (R8) added the R8 code but also included the R9 tests when the R9 code did not exist yet so the tests for R9 failes at that commit but it does not mention it anywhere. I would change it so that the commit only has the code from R8 and the tests for R8 but not the tests for R9, and instead R9 tests go with the R9 code.
 
## 5 : The function def best_entry(items): looks at a list of all the data for one excercise then prints out whichever has the heaviest weight as the personal record
	-I was right about the  way it takes entries for just one excercise and that it picks the heaviest weight as the PR.
	-I missed that it returns an entry, it does not print it
	-I missed that when there is a tie the tiebreaker is reps, then earliest date. It also convers kg to lbs to mixed units can compare.
	-I was surprised that most_improved doesnt use this function so the two can produce slightly different answers if theres a tie
