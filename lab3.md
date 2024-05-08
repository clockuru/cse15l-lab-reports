# This is Lab Report 3 - Servers and SSH Keys (Week 5)

## Part 1 - Bugs
The bug I have chosen is ArrayExamples' implementation of reverseInPlace, which improperly reverses the arrays.<br/>
1. The failure-inducing input that I found for this method was:
```
@Test
public void testReverseInPlaceOddElems() {
  int[] input1 = { 3, 1, 8 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 8, 1, 3 }, input1);
}
```
2. An input that doesn't induce a failure is:
```
@Test
public void testReverseInPlaceOneElem() {
  int[] input1 = { 3 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3 }, input1);
}
```
3. The symptom of the bug is that the program "mirrors" half of the array instead of properly reversing it. Because this only affects arrays with more than one element, the first test fails while the other one succeeds.<br/>
![Part1-Screenshot1](https://github.com/clockuru/cse15l-lab-reports/blob/main/lab4-Part1-Screenshot1.png?raw=true)<br/>
![Part1-Screenshot2](https://github.com/clockuru/cse15l-lab-reports/blob/main/lab4-Part1-Screenshot2.png?raw=true)<br/>
4. Here is the code before the change:
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
And here is the code after:
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length/2; i += 1) {
    int temp = arr[i];
    arr[i] = arr[arr.length - i - 1];
    arr[arr.length - i - 1] = temp;
  }
}
```
5. I made the program store the value of the element being reversed temporarily so that it'd be swapped simultaneously with the element on the opposite half of the array corresponding to its index. As a result, the method only needs to run on half of the array, as it would unreverse it while going through the second half.<br/>
## Part 2 - Researching Commands
The command I have chosen is `grep`. I got all of my information from running `grep --help`, which outputs information on how to use the command, listing all of its patterns as well. Extra newline characters are removed in the output in some cases.<br/>
1. `grep -i, --ignore-case`<br/>
Using the option `-i` causes `grep` to ignore the case of the pattern it is searching for. This can be useful when searching for a specific phrase in a text document that has a chance of appearing at the start of a sentence, since capitalization would alter the results without the `-i` in that case.<br/>
Example 1: Multiple capitalizations<br/>
```
$ grep -i "clinical" ./technical/biomed/1468-6708-3-1.txt
        decreased mortality. Clinical trials powered to detect
        whom risk factors, subclinical disease, and morbidity are
          baseline. Clinical covariates include hypertension,
        significantly greater than zero. A clinical trial of a
          Implications for clinical trials
          YHL, but not YOL. Clinical trials of weight modification
          found for underweight older adults. Clinical trials whose
          outcome measure. Both YOL and YHL would be clinically
        YHL as the outcome measure in clinical trials involving
```
Example 2: Ignore case in input<br/>
```
$ grep -i "HI" ./technical/secret/awesome-text-file.txt 
hi
```
2. `grep -v, --invert-match`<br/>
Using the option `-v` causes grep to output all the lines that do **not** contain the given pattern. This can be useful when sorting through a data set, such as in a CSV file, and filtering out certain entries that contain the pattern.<br/>
Example 1: Filtering out "the"<br/>
```
$ grep -v the ./technical/911report/preface.txt
            PREFACE
                Democrats chosen by elected leaders from our nation's capital at a time of great
                avoid such tragedy again?
                27, 2002).
            Our mandate was sweeping. The law directed us to investigate "facts and circumstances
                to intelligence agencies, law enforcement agencies, diplomacy, immigration issues
                reviewed more than 2.5 million pages of documents and interviewed more than 1,200
                current and previous administrations who had responsibility for topics covered in
                our mandate. We have sought to be independent, impartial, thorough, and nonpartisan.
                public testimony from 160 witnesses.
                learned.
            We learned about an enemy who is sophisticated, patient, disciplined, and lethal. The
                political grievances, but its hostility toward us and our values is limitless. Its
                and equal rights for women. It makes no distinction between military and civilian
                targets. Collateral damage is not in its lexicon.
                and national security did not understand how grave this threat could be, and did not
                fault lines within our government-between foreign and domestic intelligence, and
                sharing information across a large and unwieldy government that had been built in a
                different era to confront different dangers.
                positive-an America that is safer, stronger, and wiser. That September day, we came
                accountability.
            As we complete our final report, we want to begin by thanking our fellow
                Commissioners, whose dedication to this task has been profound. We have reasoned
                built. They have given good advice, and faithfully carried out our guidance. They
                have searched records and produced a multitude of documents for us. We thank
                This final report is only a summary of what we have done, citing only a fraction of
                issues and organizations, we are conscious of our limits. We have not interviewed
                every knowledgeable person or found every relevant piece of paper. New information
                inevitably will come to light. We present this report as a foundation for a better
            We have listened to scores of overwhelming personal tragedies and astounding acts of
                preparing to respond if it becomes necessary. We emerge from this investigation with
                this process with strong opinions about what would work. All of us have had to
                citizens to study, reflect-and act.
            Thomas H. Kean, chair
            Lee H. Hamilton, vice chair
```
Example 2: Combining with `-i`, ignoring all cases of "the"<br/>
```
$ grep -vi "THE" ./technical/plos/journal.pbio.0020353.txt
        fueled by a slew of congressional and parliamentary recommendations, claims of political
        victory by critics and proponents of open access, and redoubled lobbying efforts on every
        of public money invested in scientific research and its outputs is sufficient to merit
        Committee 2004). United States National Institutes of Health (NIH) Director Elias Zerhouni
        concerns that governments are poised to tell researchers where or how to publish seem
        legislative dictates on access to scientific literature are likely to be structured to
        minimize potentially deleterious implications for established, subscription-based journals,
        results of publicly funded research would not be mandates for scientists to submit work
        PLoS Biology and
        in centralized repositories. A US House of Representatives Committee on Appropriations, for
        example, recently passed language that would allow many, though not all, publishers six
        In any case, it is a perfectly reasonable premise that governments should attach
        conditions to grants mandating public access to resulting peer-reviewed, published
        disseminated as widely as possible is hardly a revolutionary proposition. All funders
        Central. Actually requiring that publicly funded works be
        included in publicly funded electronic archives like PubMed Central, as
        agencies.
        process. We… hope that this report will be a catalyst for change” (House of Commons Science
        and Technology Committee 2004).
        As a matter of sheer principle, it strikes many people as odd that “anyone can download
        has yet to legislate a remedy for this
        prima facie paradoxical state of affairs, both appear ready to address
        constituents: scientists, publishers, librarians, patient advocates, text-miners,
        of a seven-month investigation, featuring some 127 submissions of written evidence and four
        public access to research results seems methodical, inclusive, and likely to prove
```
3. `grep -m, --max-count=NUM`<br/>
