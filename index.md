Lab 5
Anonymous:
Hi, is it possible that I can get a hint on what was wrong with the ListExamples. java file in the Skill Demo 9 practice? I remember in week 7 the lab asked us to change index1 to index2 and that fixed the problem for the merge function, but I couldn't figure out what was wrong with the filter function.

```
student@8e71b02402ac:~/buggy$ bash test.sh
JUnit version 4.13.2
..E
Time: 0.026
There was 1 failure:
1) testFilter(TestListExamples)
java.lang.AssertionError: expected:<[apple, a]> but was:<[a, apple]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at TestListExamples.testFilter(TestListExamples.java:15)

FAILURES!!!
Tests run: 2,  Failures: 1
```
Staff:
Of course! Start by looking into what was output when you ran the test.sh file, what is wrong with the filter function? The order of appending elements to the list matters a lot in this case!

Student (fixed):
Thank you! I've figured it out! In the original code, the if statement appends the desired string to the very front of the list, which is at inde 0, but rather we want to append to the very end of the list, so the index should be the list.size().

```
student@8e71b02402ac:~/buggy$ bash test.sh
JUnit version 4.13.2
..
Time: 0.037

OK (2 tests)
```
```
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(result.size(), s);
      }
    }
    return result;
  }
```



