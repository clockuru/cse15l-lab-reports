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
I made the program store the value of the element being reversed temporarily so that it'd be swapped simultaneously with the element on the opposite half of the array corresponding to its index. As a result, the method only needs to run on half of the array, as it would unreverse it while going through the second half.
