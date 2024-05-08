# This is Lab Report 3 - Servers and SSH Keys (Week 5)

## Part 1 - Bugs
The bug I have chosen is ArrayExamples' implementation of reverseInPlace, which causes it to "mirror" half of the array instead of properly reversing it.<br/>
1. The failure-inducing input that I found for this method was:
```
@Test
public void testReverseInPlaceOddElems() {
  int[] input1 = { 3, 1, 8 };
  ArrayExamplesOld.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 8, 1, 3 }, input1);
}
```
2. An input that doesn't induce a failure is:
```
@Test
public void testReverseInPlaceOneElem() {
  int[] input1 = { 3 };
  ArrayExamplesOld.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3 }, input1);
}
```
3. 
