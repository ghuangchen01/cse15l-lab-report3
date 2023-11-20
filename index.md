<h1>Lab Report 3</h1>
<h2>Part 1 Bugs</h2>
<h3>A failure-inducing input:</h3>
<br/>
```java
  @Test
  public void testReversed() {
    int[] input1 = {1,2,3,4,5};
    assertArrayEquals(new int[]{5,4,3,2,1}, ArrayExamples.reversed(input1));
  }
```
<p>The result is:</p>
![Image](failure_result.png)
<h3>An input that doesn't induce a failure:</h3>
```java
 @Test
  public void testReversed() {
    int[] input1 = {};
    assertArrayEquals(new int[]{}, ArrayExamples.reversed(input1));
  }
```
<p>The result is:</p>
![Image](failure_result.png)
<p>The symptom is:</p>
![Image](test_symptom.png)

<p>Code with bug:</p>
```java

  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
  
```
<p>The code fix with switching newArray and arr, also the return changes to newArray:</p>

```java

  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length-1-i];
    }
    return newArray;
  }

```
<p>Success Test:</p>
![Image](test_success.png)
<h3>Describe why the fix addresses the issue:</h3>
The code before fix, inside the `for loop` the array `arr` is the one who changes. `newArray` is new created and it is empty. For every `i` the array `arr` is setting the value to `newArray` which are all 0s. After fixing the problem by switching their position, now `newArray` will store the integers in `arr` in a reverse order. At the end, I changed the `return arr` to `return newArray` to return the correct array result.

<h2>Part 2 Researching Commands</h2>
<h3>grep -ro 'Small' ./technical </h3>

<p>Doing recursive search on all the files and look at each line to search for 'Small', the result would be printing all the paths of the lines that contains the word in files without the text. -ro is a combination of -r and -o, -r is searching recursively, -o is output path but without the text that matches the word.</p>

```java
guan@Guanhaos-MBP docsearch % grep -ro 'Small' ./technical
./technical//government/Env_Prot_Agen/multi102902.txt:Small
./technical//government/Env_Prot_Agen/ctf1-6.txt:Small
./technical//government/Env_Prot_Agen/1-3_meth_901.txt:Small
./technical//government/Env_Prot_Agen/atx1-6.txt:Small
./technical//government/Gen_Account_Office/d0269g.txt:Small
./technical//government/Gen_Account_Office/Testimony_cg00010t.txt:Small
./technical//government/Gen_Account_Office/og97032.txt:Small
./technical//government/Gen_Account_Office/og99036.txt:Small
./technical//government/Gen_Account_Office/og99036.txt:Small
./technical//government/Gen_Account_Office/d01376g.txt:Small
./technical//government/Gen_Account_Office/pe1019.txt:Small
./technical//government/Gen_Account_Office/pe1019.txt:Small
./technical//government/Gen_Account_Office/d01121g.txt:Small
./technical//government/Gen_Account_Office/og96011.txt:Small
./technical//government/Gen_Account_Office/og96011.txt:Small
./technical//government/Gen_Account_Office/og97051.txt:Small
./technical//government/Gen_Account_Office/Testimony_d01609t.txt:Small
./technical//government/Gen_Account_Office/og97050.txt:Small
./technical//government/Gen_Account_Office/og96012.txt:Small
./technical//government/Gen_Account_Office/og96012.txt:Small
./technical//government/Gen_Account_Office/og96012.txt:Small
./technical//government/Gen_Account_Office/og97052.txt:Small
./technical//government/Gen_Account_Office/June30-2000_gg00135r.txt:Small
./technical//government/Gen_Account_Office/June30-2000_gg00135r.txt:Small
./technical//government/Gen_Account_Office/June30-2000_gg00135r.txt:Small
./technical//government/Gen_Account_Office/June30-2000_gg00135r.txt:Small
./technical//government/Gen_Account_Office/og96028.txt:Small
./technical//government/Gen_Account_Office/og96014.txt:Small
./technical//government/Gen_Account_Office/og96015.txt:Small
./technical//government/Gen_Account_Office/og96031.txt:Small
./technical//government/Gen_Account_Office/og96033.txt:Small
./technical//government/Gen_Account_Office/og96027.txt:Small
./technical//government/Gen_Account_Office/og96027.txt:Small
./technical//government/Gen_Account_Office/og98022.txt:Small
./technical//government/Gen_Account_Office/og96026.txt:Small
./technical//government/Gen_Account_Office/og96026.txt:Small
./technical//government/Gen_Account_Office/og96032.txt:Small
./technical//government/Gen_Account_Office/og96036.txt:Small
./technical//government/Gen_Account_Office/og96022.txt:Small
./technical//government/Gen_Account_Office/og96023.txt:Small
./technical//government/Gen_Account_Office/og96037.txt:Small
./technical//government/Gen_Account_Office/og96037.txt:Small
./technical//government/Gen_Account_Office/og98024.txt:Small
./technical//government/Gen_Account_Office/og96021.txt:Small
./technical//government/Gen_Account_Office/og96020.txt:Small
./technical//government/Gen_Account_Office/og96047.txt:Small
./technical//government/Gen_Account_Office/og98044.txt:Small
./technical//government/Gen_Account_Office/og96040.txt:Small
./technical//government/Gen_Account_Office/og97003.txt:Small
./technical//government/Gen_Account_Office/og96043.txt:Small
./technical//government/Gen_Account_Office/og96043.txt:Small
./technical//government/Post_Rate_Comm/ReportToCongress2002WEB.txt:Small
./technical//government/Media/Law_Schools.txt:Small
./technical//government/Media/Working_for_Free.txt:Small
./technical//government/Media/Disaster_center.txt:Small
./technical//government/Media/Using_Tech_Tools.txt:Small
./technical//government/Media/pro_bono_efforts.txt:Small
./technical//plos/journal.pbio.0020431.txt:Small
./technical//plos/pmed.0020075.txt:Small
./technical//plos/pmed.0020075.txt:Small
./technical//plos/journal.pbio.0020311.txt:Small
./technical//plos/journal.pbio.0020214.txt:Small
./technical//plos/pmed.0020242.txt:Small
./technical//biomed/1471-2199-2-10.txt:Small
./technical//biomed/1471-2334-3-9.txt:Small
./technical//biomed/1472-6947-3-8.txt:Small
./technical//biomed/1471-2229-2-3.txt:Small
./technical//biomed/1472-6785-1-3.txt:Small
./technical//biomed/gb-2001-2-8-research0027.txt:Small
./technical//biomed/gb-2003-4-5-r32.txt:Small
./technical//biomed/cc3.txt:Small
./technical//biomed/1471-2431-2-4.txt:Small
./technical//biomed/1471-2202-4-17.txt:Small
./technical//biomed/1471-2474-2-2.txt:Small
./technical//biomed/cc2190.txt:Small
./technical//biomed/1471-2105-3-12.txt:Small
./technical//biomed/gb-2001-2-9-research0035.txt:Small
./technical//biomed/bcr285.txt:Small
./technical//biomed/1472-6890-1-4.txt:Small
./technical//biomed/1471-2172-3-10.txt:Small
./technical//biomed/1472-6904-1-2.txt:Small
./technical//biomed/1471-213X-1-2.txt:Small
./technical//biomed/1471-2458-2-6.txt:Small
./technical//biomed/1471-2202-2-17.txt:Small
./technical//biomed/gb-2002-3-12-research0083.txt:Small
./technical//biomed/gb-2002-3-12-research0080.txt:Small
./technical//biomed/1471-2164-4-15.txt:Small
./technical//biomed/1477-7827-1-6.txt:Small
./technical//biomed/1475-4924-1-10.txt:Small
./technical//biomed/1471-2148-1-14.txt:Small
./technical//biomed/1471-2407-2-19.txt:Small
./technical//biomed/1471-2407-2-19.txt:Small
./technical//biomed/1471-2334-2-24.txt:Small
./technical//biomed/1471-2156-2-12.txt:Small
./technical//biomed/gb-2002-3-12-research0071.txt:Small
./technical//biomed/1476-4598-2-1.txt:Small
./technical//biomed/1471-2180-1-26.txt:Small
./technical//biomed/1471-2121-2-15.txt:Small
./technical//biomed/1471-2164-3-31.txt:Small
./technical//biomed/1472-6793-2-18.txt:Small
./technical//biomed/1471-2164-3-24.txt:Small
./technical//biomed/1471-2180-2-1.txt:Small
./technical//biomed/1471-2180-2-1.txt:Small
./technical//biomed/1471-2091-3-4.txt:Small
./technical//biomed/1471-2091-3-4.txt:Small
./technical//biomed/1471-2091-3-4.txt:Small
./technical//biomed/1471-2091-3-4.txt:Small
./technical//biomed/1472-6793-2-5.txt:Small
./technical//biomed/gb-2001-2-12-research0054.txt:Small
./technical//biomed/gb-2001-2-12-research0054.txt:Small
./technical//biomed/gb-2001-2-12-research0054.txt:Small
./technical//biomed/1471-2202-2-2.txt:Small
./technical//biomed/1471-2121-4-6.txt:Small
./technical//biomed/1472-6947-1-5.txt:Small
./technical//biomed/1471-2202-4-2.txt:Small
./technical//911report/chapter-13.4.txt:Small
./technical//911report/chapter-13.4.txt:Small
./technical//911report/chapter-13.4.txt:Small
./technical//911report/chapter-13.4.txt:Small
./technical//911report/chapter-13.4.txt:Small
./technical//911report/chapter-13.4.txt:Small
./technical//911report/chapter-13.5.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-13.3.txt:Small
./technical//911report/chapter-3.txt:Small
./technical//911report/chapter-3.txt:Small
./technical//911report/chapter-3.txt:Small
./technical//911report/chapter-3.txt:Small
./technical//911report/chapter-3.txt:Small
./technical//911report/chapter-3.txt:Small
./technical//911report/chapter-3.txt:Small
./technical//911report/chapter-3.txt:Small
./technical//911report/chapter-3.txt:Small
./technical//911report/chapter-5.txt:Small
./technical//911report/chapter-6.txt:Small
./technical//911report/chapter-6.txt:Small
./technical//911report/chapter-6.txt:Small
./technical//911report/chapter-6.txt:Small
./technical//911report/chapter-6.txt:Small
./technical//911report/chapter-11.txt:Small
```
<p>It prints the path of the files, and by how many times the file repeats means how many lines contains the word in technical folder.</p>

<h3>grep -ro 'Small' ./technical/911report </h3>
<p>Print all the file paths in repeating times depending on how many line would contain the word 'Samll'</p>
```java
guan@Guanhaos-MBP docsearch % grep -ro 'Small' ./technical/911report
./technical/911report/chapter-13.4.txt:Small
./technical/911report/chapter-13.4.txt:Small
./technical/911report/chapter-13.4.txt:Small
./technical/911report/chapter-13.4.txt:Small
./technical/911report/chapter-13.4.txt:Small
./technical/911report/chapter-13.4.txt:Small
./technical/911report/chapter-13.5.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-13.3.txt:Small
./technical/911report/chapter-3.txt:Small
./technical/911report/chapter-3.txt:Small
./technical/911report/chapter-3.txt:Small
./technical/911report/chapter-3.txt:Small
./technical/911report/chapter-3.txt:Small
./technical/911report/chapter-3.txt:Small
./technical/911report/chapter-3.txt:Small
./technical/911report/chapter-3.txt:Small
./technical/911report/chapter-3.txt:Small
./technical/911report/chapter-5.txt:Small
./technical/911report/chapter-6.txt:Small
./technical/911report/chapter-6.txt:Small
./technical/911report/chapter-6.txt:Small
./technical/911report/chapter-6.txt:Small
./technical/911report/chapter-6.txt:Small
./technical/911report/chapter-11.txt:Small
```
<p>It prints the path of the files, and by how many times the file repeats means how many lines contains the word in 911report folder inside technical folder.</p>

<h3>grep -ri 'hello' ./technical</h3>
<p>The -i option makes the search case-insensitive. This means it will match 'Hello', 'HELLO', 'hello', and any other case variations in the technical folder's file because of -r recursive search.</p>

```java
guan@Guanhaos-MBP docsearch % grep -ri 'hello' ./technical
./technical/911report/chapter-1.txt:    At 10:39, the Vice President updated the Secretary on the air threat conference: Vice President: There's been at least three instances here where we've had reports of aircraft approaching Washington-a couple were confirmed hijack. And, pursuant to the President's instructions I gave authorization for them to be taken out. Hello?
```
<p>It outputs the file path and the search result. We can see that in this paragraph, the word is Hello but using -i it still works.</p>

<h3>grep -ri 'hello' ./technical/911report</h3>
<p>The -i option makes the search case-insensitive. This means it will match 'Hello', 'HELLO', 'hello', and any other case variations in the technical folder's 911repot folder's file because of -r recursive search.</p>
```java
guan@Guanhaos-MBP docsearch % grep -ri 'hello' ./technical/911report
./technical/911report/chapter-1.txt:    At 10:39, the Vice President updated the Secretary on the air threat conference: Vice President: There's been at least three instances here where we've had reports of aircraft approaching Washington-a couple were confirmed hijack. And, pursuant to the President's instructions I gave authorization for them to be taken out. Hello?
```
<p>It prints the same result because there is only one file containing the word Hello.</p>

<h3>grep -row 'talk' ./technical</h3>
<p>Using -w ensures that grep matches the whole word 'talk'. Without this option, 'talk' might also match words like 'talking' or 'talks'. -ro is already explained on example one and two.</p>

```java
guan@Guanhaos-MBP docsearch % grep -row 'talk' ./technical
./technical/government/About_LSC/commission_report.txt:talk
./technical/government/About_LSC/ONTARIO_LEGAL_AID_SERIES.txt:talk
./technical/government/About_LSC/diversity_priorities.txt:talk
./technical/government/About_LSC/State_Planning_Report.txt:talk
./technical/government/Gen_Account_Office/ai9868.txt:talk
./technical/government/Gen_Account_Office/May1998_ai98068.txt:talk
./technical/government/Post_Rate_Comm/Gleiman_EMASpeech.txt:talk
./technical/government/Post_Rate_Comm/Gleiman_EMASpeech.txt:talk
./technical/government/Post_Rate_Comm/Gleiman_EMASpeech.txt:talk
./technical/government/Post_Rate_Comm/Mitchell_6-17-Mit.txt:talk
./technical/government/Media/Unusual_Woodburn.txt:talk
./technical/government/Media/Lindsays_legacy.txt:talk
./technical/government/Media/Lindsays_legacy.txt:talk
./technical/government/Media/Paralegal_Honored.txt:talk
./technical/government/Media/Texas_Lawyer.txt:talk
./technical/government/Media/Funds_Shortage.txt:talk
./technical/government/Media/Avoids_Budget_Cut.txt:talk
./technical/government/Media/Assuring_Underprivileged.txt:talk
./technical/government/Media/Firm_to_the_Poor_Needs_Help.txt:talk
./technical/government/Media/Local_Attorneys.txt:talk
./technical/government/Media/Library_Lawyers.txt:talk
./technical/government/Media/Pro-bono_road_show.txt:talk
./technical/plos/pmed.0020203.txt:talk
./technical/plos/journal.pbio.0020262.txt:talk
./technical/plos/journal.pbio.0020311.txt:talk
./technical/plos/journal.pbio.0020311.txt:talk
./technical/plos/journal.pbio.0020310.txt:talk
./technical/plos/journal.pbio.0020064.txt:talk
./technical/plos/pmed.0010042.txt:talk
./technical/plos/pmed.0020209.txt:talk
./technical/plos/journal.pbio.0020012.txt:talk
./technical/biomed/1471-2407-3-18.txt:talk
./technical/biomed/1471-244X-2-9.txt:talk
./technical/biomed/1472-6815-2-3.txt:talk
./technical/biomed/1471-2458-2-25.txt:talk
./technical/biomed/1472-6947-2-7.txt:talk
./technical/biomed/1472-6963-3-14.txt:talk
./technical/biomed/1472-6963-3-14.txt:talk
./technical/biomed/1475-925X-2-3.txt:talk
./technical/biomed/1471-213X-2-8.txt:talk
./technical/biomed/1477-7827-1-23.txt:talk
./technical/biomed/1471-2164-2-2.txt:talk
./technical/biomed/gb-2002-3-10-research0056.txt:talk
./technical/biomed/1471-2202-3-17.txt:talk
./technical/biomed/1478-1336-1-3.txt:talk
./technical/biomed/1476-4598-1-6.txt:talk
./technical/911report/chapter-13.5.txt:talk
./technical/911report/chapter-13.5.txt:talk
./technical/911report/chapter-13.3.txt:talk
./technical/911report/chapter-3.txt:talk
./technical/911report/chapter-1.txt:talk
./technical/911report/chapter-1.txt:talk
./technical/911report/chapter-1.txt:talk
./technical/911report/chapter-9.txt:talk
```
<p>It outputs all the paths of lines that has the word exact match to word 'talk' in the files inside technical folder</p>
<h3>grep -row 'talk' ./technical/biomed</h3>
<p>Search the word 'talk in files inside biomed folder inside technical folder</p>
```java
guan@Guanhaos-MBP docsearch % grep -row 'talk' ./technical/biomed
./technical/biomed/1471-2407-3-18.txt:talk
./technical/biomed/1471-244X-2-9.txt:talk
./technical/biomed/1472-6815-2-3.txt:talk
./technical/biomed/1471-2458-2-25.txt:talk
./technical/biomed/1472-6947-2-7.txt:talk
./technical/biomed/1472-6963-3-14.txt:talk
./technical/biomed/1472-6963-3-14.txt:talk
./technical/biomed/1475-925X-2-3.txt:talk
./technical/biomed/1471-213X-2-8.txt:talk
./technical/biomed/1477-7827-1-23.txt:talk
./technical/biomed/1471-2164-2-2.txt:talk
./technical/biomed/gb-2002-3-10-research0056.txt:talk
./technical/biomed/1471-2202-3-17.txt:talk
./technical/biomed/1478-1336-1-3.txt:talk
./technical/biomed/1476-4598-1-6.txt:talk
```
<p>It outputs all the paths of lines that has the word exact match to word 'talk' in the files inside biomed folder inside technical folder</p>
