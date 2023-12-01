Lab 5


Part 1


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
I would suggest you start by looking into what was output when you ran the test.sh file, what is wrong with the filter function? The order of appending elements to the list matters a lot in this case!

Student (fixed):
Thank you! I've figured it out! In the original code, the if statement appends the desired string to the very front of the list, which is at index 0, but rather we want to append to the very end of the list, so the index should be the list.size().

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
The directory is buggy, and we are running the test.sh and ListExamples.java file in the buggy directory. The test.sh was just the commands that triggered the bug and produced the output, it contains no bug. However, we were trying to fix the ListExamples.java file. In the ListExamples.java file, which contains two functions, filter and merge; in this scenario, the student has already fixed the bug in the merge function but is stuck on debugging for the filter function. The error message output by running test.sh that said the order of the list was wrong, but the student didn't know how to fix that. The command line I ran was
```
student@8e71b02402ac:~/buggy$ bash test.sh
```
It triggered the bug, and produced the output telling us that the JUnit failed. 
Part 2 – Reflection
I have never used Linux before, so it was very challenging and interesting to learn it from scratch. I think something I found very unique was how we learned how to start a server that pops up a website when it starts. I think something really cool that we did in the lab was when we worked in pairs trying to imitate and build our grading system and we ran the different repositories to check its functionality. Also, the process of debugging with Vim was a very new experience for me because of the unique command keys for Vim, and it was very surprising for me that the cursor didn't work in Vim. 

