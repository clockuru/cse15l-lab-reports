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
3. The symptom of the bug is that the program "mirrors" half of the array instead of properly reversing it
