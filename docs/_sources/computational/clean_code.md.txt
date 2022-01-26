
# Clean code

```{note}
  Aim: The following are notes from the Clean Code book by Robert C. Martin. The aim is to briefly cover some best coding practices on simple 
  examples.

  Level: any 🌱🌿🌳
```

## Chapter 1: Meaningful names

### Use intention-revealing names
Names should reveal intent.

```python
# bad
def check(d, d2):
    if d2 in d:
        return True
    return False 

# good
def sequence_has_subsequence(sequence, subsequence):
    if subsequence in sequence:
        return True
    return False


if sequence_has_subsequence("ACTGACTG", "ACT"):
    print("We have a match")
```

### Avoid disinformation
* Don't call something a list unless it's actually a list
* Avoid long variable names that are similar

### Make meaningful distinctions
```python
# bad
def align_sequence_to_reference(dna1, dna2):
    # ..

# Good
def align_sequence_to_reference(reference_dna, query_dna):
    # ..
```

Avoid noise words:
```python
dna_string = "ACTG"
# instead:
dna = "ACTG"
```


### Use pronounceable names
```python
# bad
mcfdrsmplrate = 3.0

# good
monte_carlo_false_discovery_sample_rate = 3.0
# or maybe
mc_false_discovery_sample_rate = 3.0
```

### Use searchable names
* Only use single-letter names as local variables inside short methods
* Variables used multiple places should have a search-friendly name

### Avoid mental mapping
```python
# bad

j = 4.0
for s in range(n_samples):
    for i in range(0, 100):
        analyse_sample(s, i, j)

# better
analysis_parameter = 4.0
for sample_id in range(n_samples):
    for analysis_iteration in range(0, 100):
        analyse_sample(sample_id, analysis_iteration, analysis_parameter)
```

### Classes and objects should have noun names
```python
# bad (avoid verbs)
class Analyse:

# good
class ImmuneAnalysisRunner:
```

### Methods should have verb or verb phrases as names
```python
# bad 
def figure(data):

# good
def make_figure(data):

# .. or e.g.:
def get_figure(data):
```

### Don't be cute
This example is taken from Telia code base for sending an invoice:
```python
# bad 
class QuantumOfSolace:
    def send_to_customer(self):
    
# good
class Invoice:
    def send_to_customer(self):
```

### Pick one word per concept
```python
# bad
class Sample:
    def get_sample(self):

class Analysis:
    def fetch_analysis(self):
```

### Other rules:
* Avoid using the same word for two purposes
* Use solution domain names (okay to use computer science terminology)
* Add meaningful contect (example: a class can give context to a method)


## Chapter 3: Functions
### Make functions small

### Keep indentation level at maximum 1 or 2
Everything further intendented can usually be a new function

### Functions should do one thing
Functions should do one thing. They should do it well. They should do it only.
A function can do multiple things if they are at the same level of abstraction.

* "Only one level of abstraction per function"
```python
# bad
class Samples:
    def add_sample(self, sample):
        # add
        self.samples.append(sample)

        # run analysis on this sample
        for s in self.other_samples:
            simulated_data = self.get_simulated_data(s)
            results = self.analyse_two_samples(sample, s)
            for result in results:
                if result > self.best_result:
                    best_result = result
            
        # print report
        .... 

# better (but not good)
class Samples:
    def add_sample(self, sample):
        self.samples.append(sample)
        analysis = self.analyse(sample)
        self.print_report(analysis)

# good: Do not analyse anything in the add method
```

### The stepdown-rule
Every function should be followed by a next one so that we can read and understand the code from top to bottom.

```python
class SampleAnalyser:
    def add_sample(self):
    
    def filter_sample(self):

    def analyse_sample(self):

    def print_analysis_report(self):
```

### Give your functions few arguments
* Zero arguments is optimal
* No more than 3 arguments
  * When more than 3: Wrap arguments in a class of their own

(This rule might be up for discussion, since IDE's and optional arguments in Python makes many arguments less of a problem)

### Flag arguments are ugly
"Passing a boolean into a function is a truly terrible practice"

* Instead: Make multiple functions

###  Functions should not have side effects
Example: See the previous `add_sample` method 

### Functions should either do something or answer something (not both)

### Prefer exceptions to returning error codes
```python
# bad
def add_sample(self, sample):
    if self.has_sample(sample):
        return 503
    
    self.samples.append(sample)
    return 1

# good
def add_sample(self, sample):
    if self.has_sample(sample):
        raise DuplicateSampleException("Sample %s already exists and cannot be added" % s)
    
    self.samples.append(sample)
```

### Extract try/catch blocks
Don't do error handling inside function that do a specific task (have try/catch on the outside)

### Don't repeat yourself

### (Optional) All functions should have one entry and one exit
* No continue, break or early returns
* Only one return
```python
# instead of this
def has_sample(self, sample):
    for other_sample in self.samples:
        if sample  == other_sample:
            return True
        
    return False

# .. do this:
def has_sample(self, sample):
    has_sample = False
    for other_sample in self.samples:
        if sample == other_sample:
            has_sample = True
            # break would be discouraged here ?
            
    return has_sample
```

### Refine long functions into multiple shorter
It is okay and common to start out writing long functions, and then refactor them.



## Chapter 4: Comments
"Don't comment bad code -- rewrite it."
* Comments "compensate" for failure to express ourself in code
* "Comments lie"
* Code changes and evolve, comments stay behind
* Inaccurate comments are far worse than no comments at all

### Comments do not make up for bade code
* Clean up your bad code instead of commenting it
  * *How do we relate this with "quick and dirty programming?"*

### Explain your self in code

### Don't use comments when you can use a function or variable
```python
# bad
# get the sample
s = pd.read_some_format("data.txt", skip_header=True, sep=",")
# analyse sample
for i in range(n):
    # ... 
    #.. 

# good
sample = get_sample()
analyse(sample)
```

### Avoid noise
```python
# sample
sample = get_sample()
# analyse
analyse(sample)
```

### Avoid todo comments
Use external systems instead.

### Informative comments
* Can be useful for cryptic code that cannot be written clearly.
* Can be useful to comment use of library functions/classes
* Amplify something that's important ("trimming sequence is important to avoid bug ...")

### Don't comment out code
Remove it and use version control instead.


## Chapter 5: Formatting

The purpose of good formating is give a good impression about the neatness and consistency of the code.

### Vertical formatting

- No hard and fast rule
- Small files are usually easier to understand ~200 lines. 

#### The Newspaper Metaphor (structure)

- Headline: what the story is about 
- First paragraph: synopsis/bird's-eye view of the story
- The rest: all the details

Similarly, in a source file:

- Name should be simple and tell us whether we are in the
right module or not. 
- The topmost parts of the source file should provide the high-level
concepts. 
- Detail should increase as we move downward.


#### The Newspaper Metaphor (length of files)

- Most articles are very small. 
- Some are a bit larger. 
- Very few contain as much text as a page can hold.

#### Vertical Openness Between Concepts

```python
# bad
import numpy.random as rn
def get_rand_int(h):
    return rn.randint(0, h)
def get_normal(s):
    return rn.normal(0, s)
```
```python
# good
import numpy.random as rn

def get_rand_int(h):
    return rn.randint(0, h)

def get_normal(s):
    return rn.normal(0, s)
```
#### Vertical Density

If openness separates concepts, then vertical density implies close association.

```java
// bad
public class ReporterConfig {
 /**
 * The class name of the reporter listener
 */
 private String m_className;
 /**
 * The properties of the reporter listener
 */
 private List<Property> m_properties = new ArrayList<Property>();
 public void addProperty(Property property) {
 m_properties.add(property);
 }
```

```java
// good
public class ReporterConfig {
 private String m_className;
 private List<Property> m_properties = new ArrayList<Property>();
 
 public void addProperty(Property property) {
 m_properties.add(property);
 }
```

#### Vertical Distance

Concepts that are closely related should be kept vertically close to each other.

##### Variable Declarations
Variables should be declared as close to their usage as possible.

#### Vertical ordering (language dependent)
- Functions should be defined below the functions that call it
- This is the exact opposite of languages like C and C++ that enforce functions to be defined, or at least declared,
before they are used.

### Horizontal Formatting

No hard rules, especially as monitors can be too wide, and the font size is adjustable.

Rule of thumb: 120 characters

#### Horizontal Openness and Density

Horizontal white space to associate things that are strongly related and disassociate
things that are more weakly related.

```python
# bad
class Quadratic():
 def __init__ (self,...):
     ⋮
 def root1 (self, a, b, c):
  determinant=self.determinant(a, b, c)
  return (-b+math.sqrt(determinant))/(2 * a)

 def determinant (self, a, b, c):
  return b*b-4*a*c
```
```python
# good
class Quadratic():
 def __init__(self,...):
     ⋮
 def root1(self, a, b, c): # no separation between function name and parentheses
  determinant = self.determinant(a, b, c) # spaces before and after assignment operators
  return (-b - math.sqrt(determinant)) / (2*a) # spaces to accentuate the precedence of operators, and clarify the operations

 def determinant(self, a, b, c):
  return b*b - 4*a*c
```

Unfortunately, most tools for reformatting code are blind to the precedence of
operators and impose the same spacing throughout. So subtle spacings like those
shown above tend to get lost after you reformat the code.

#### Horizontal Alignment
Assembly language-inspired alignment

```java
// bad
public class FitNesseExpediter implements ResponseSender
{
    private     Socket          socket;
    private     InputStream     input;
    private     OutputStream    output;
    private     Request         request;
    
    public FitNesseExpediter(Socket s,
                             FitNesseContext context) // throws Exception
    {
    this.context =              context;
    socket =                    s;
}
```

```java
// good
public class FitNesseExpediter implements ResponseSender
{
    private Socket socket;
    private InputStream input;
    private OutputStream output;
    private Request request;
    
    public FitNesseExpediter(Socket s, FitNesseContext context)
    {
    this.context = context;
    socket = s;
}
```

#### Indentation
A source file is a hierarchy rather like an outline. 

Each level of this hierarchy is a scope into which:
- names can be declared
- declarations and executable statements are interpreted. 

Therefore, we indent the lines in proportion to their position in the hiearchy:
- Statements at the level of the file, e.g. class declarations, are not indented at all. 
- Methods within a class are indented one level to the right of the class. 
- Implementations of those methods are implemented one level to the right of the method declaration. 

```java
public class FitNesseServer implements SocketServer { private FitNesseContext
context; public FitNesseServer(FitNesseContext context) { this.context =
context; } public void serve(Socket s) { serve(s, 10000); } public void
serve(Socket s, long requestTimeout) { try { FitNesseExpediter sender = new
FitNesseExpediter(s, context);
sender.setRequestParsingTimeLimit(requestTimeout); sender.start(); }
catch(Exception e) { e.printStackTrace(); } } }
```

```java
public class FitNesseServer implements SocketServer {
  private FitNesseContext context;

  public FitNesseServer(FitNesseContext context) {
    this.context = context;
  }
 
  public void serve(Socket s) {
    serve(s, 10000);
  }
 
  public void serve(Socket s, long requestTimeout) {
    try {
      FitNesseExpediter sender = new FitNesseExpediter(s, context);
      sender.setRequestParsingTimeLimit(requestTimeout);
      sender.start();
    }
    catch (Exception e) {
      e.printStackTrace();
    }
  }
}
```

##### Breaking Indentation
It is sometimes tempting to break the indentation rule for short
if statements, short while loops, or short functions.

Recommendation: Avoid collapsing scopes down to one line, and expand and indent the scopes instead, as described earlier.

## Chapter 9: Unit Tests

### The Three Laws of TDD (Test Driven Development)

- First Law: You may not write production code until you have written a failing unit test. 
- Second Law: You may not write more of a unit test than is sufficient to fail, and not compiling is failing. 
- Third Law: You may not write more production code than is sufficient to pass the currently failing test.

### Keeping Tests Clean: No quick and dirty tests

Quick and dirty tests: variables are not well named, test functions are not short and descriptive.

**Issues**:
- Having dirty tests is equivalent to, if not worse than, having no tests. 
- Tests must change as the production code evolves. The dirtier the tests, the harder they are to change.
- As you modify the production code, old tests start to fail, and the mess in the test code makes it hard to get those tests to pass again.

Verdict: test code is just as important as production code, and it is not a second-class citizen.

### Clean Tests

What makes a clean test? Three things. Readability, readability, and readability.

Don't write a test where the reader is inundated with details that must be understood before the tests make any sense.
(**show java files**)

#### BUILD-OPERATE-CHECK pattern


The first part builds up the test data:

```java
public void testGetPageHieratchyAsXml() throws Exception {
 makePages("PageOne", "PageOne.ChildOne", "PageTwo");
 ```

The second part operates on that test data:
```java
 submitRequest("root", "type:pages");
```
The third part checks that the operation yielded the expected results:
```java
 assertResponseIsXML();
 assertResponseContains(
 "<name>PageOne</name>", "<name>PageTwo</name>", "<name>ChildOne</name>"
```

#### A Dual Standard

Test code must still be simple, succinct, and expressive, but it need not be as efficient as
production code.

There are things that you might never do in a
production environment that are perfectly fine in a test environment.

##### Readability

Before:
```java
@Test
 public void turnOnLoTempAlarmAtThreashold() throws Exception {
 hw.setTemp(WAY_TOO_COLD);
 controller.tic();
 
 assertTrue(hw.heaterState());
 assertTrue(hw.blowerState());
 assertFalse(hw.coolerState());
 assertFalse(hw.hiTempAlarm());
 assertTrue(hw.loTempAlarm());
 }
```
After:
```java
@Test
 public void turnOnLoTempAlarmAtThreshold() throws Exception {
 wayTooCold();
 assertEquals("HBchL", hw.getState());
 }
```

Another example:
```java
@Test
 public void turnOnHeaterAndBlowerIfTooCold() throws Exception {
 tooCold();
 assertEquals("HBchl", hw.getState());
 }
```

Even though this is close to a violation of the rule about mental mapping, it seems
appropriate in this case. Notice, once you know the meaning, your eyes glide across
that string and you can quickly interpret the results.

##### Efficiency
```java
public String getState() {
 String state = "";
 state += heater ? "H" : "h";
 state += blower ? "B" : "b";
 state += cooler ? "C" : "c";
 state += hiTempAlarm ? "H" : "h";
 state += loTempAlarm ? "L" : "l";
 return state;
 }
```

`StringBuffers` would have been more efficient. However, the test environment, is not likely to be
constrained.

##### Verdict:
There are things that you might never do in a production environment that are perfectly fine in a test environment. Usually they involve
issues of memory or CPU efficiency. But they never involve issues of **cleanliness**.

### One Assert per Test (soft requirement)

```java
// relatively bad

public void testGetPageHieratchyAsXml() throws Exception {
 makePages("PageOne", "PageOne.ChildOne", "PageTwo");
 
 submitRequest("root", "type:pages");
 
 assertResponseIsXML();
 
 assertResponseContains(
 "<name>PageOne</name>", "<name>PageTwo</name>", "<name>ChildOne</name>"
 );
 }
 ```

 ```java
 // relatively good
 
 // first assert
 public void testGetPageHierarchyAsXml() throws Exception {
 
 givenPages("PageOne", "PageOne.ChildOne", "PageTwo");
 
 whenRequestIsIssued("root", "type:pages");
 
 thenResponseShouldBeXML();
 }
 
// second assert
 public void testGetPageHierarchyHasRightTags() throws Exception {
 
 givenPages("PageOne", "PageOne.ChildOne", "PageTwo");
 
 whenRequestIsIssued("root", "type:pages");
 
 thenResponseShouldContain(
 "<name>PageOne</name>", "<name>PageTwo</name>", "<name>ChildOne</name>"
 );
 }
```
Notice the `given-when-then` naming pattern.

Drawback: duplicate code

#### Possible solutions

1- Use the TEMPLATE METHOD pattern and put the **given**/**when** parts in the base class, and the **then** parts in different derivatives  
2- Create a completely separate test class and put the **given**/**when** parts in the @Before function, and the **then** parts in each @Test function. 

Here, this seems like too much mechanism for such a minor issue, and you could stick to multiple `asserts`.

**Verdict**: the best thing we can say is that the number of asserts in a test ought to be minimized.

### Single Concept per Test

```java
/**
 * Miscellaneous tests for the addMonths() method.
 */
 public void testAddMonths() {
     SerialDate d1 = SerialDate.createInstance(31, 5, 2004);
     
     SerialDate d2 = SerialDate.addMonths(1, d1);
     assertEquals(30, d2.getDayOfMonth());
     assertEquals(6, d2.getMonth());
     assertEquals(2004, d2.getYYYY());
     
     SerialDate d3 = SerialDate.addMonths(2, d1);
     assertEquals(31, d3.getDayOfMonth());
     assertEquals(7, d3.getMonth());
     assertEquals(2004, d3.getYYYY());
     
     SerialDate d4 = SerialDate.addMonths(1, SerialDate.addMonths(1, d1));
     assertEquals(30, d4.getDayOfMonth());
     assertEquals(7, d4.getMonth());
     assertEquals(2004, d4.getYYYY());
 }
 ```
**Concepts:**

• Given the last day of a month with 31 days (like May):
1. When you add one month, such that the last day of that month is the 30th
(like June), then the date should be the 30th of that month, not the 31st.
2. When you add two months to that date, such that the final month has 31 days,
then the date should be the 31st.

• Given the last day of a month with 30 days in it (like June):
1. When you add one month such that the last day of that month has 31 days, then the
date should be the 30th, not the 31st.

**Proposed change:**
You should test just **one concept per test** function.

### F.I.R.S.T.
 The other five rules for clean tests:
 
- **Fast:**
  - They should run quickly. 
  - When tests run slow, you won’t want to run them frequently. 
  - If you don’t run them frequently, you won’t find problems early
  enough to fix them easily. 
  - You won’t feel as free to clean up the code.
  - Eventually the code will begin to rot.


- **Independent:**
  - One test should not set up the conditions for the next test. 
  - You should be able to run each test independently and run the tests in
  any order you like. 
  - When tests depend on each other, then the first one to fail causes a cascade of downstream failures, making diagnosis difficult and hiding downstream defects.


- **Repeatable:** 
  - Tests should be repeatable in any environment. 
  - You should be able to run the
  tests in the production environment, in the QA environment, and on your laptop while
  riding home on the train without a network. 
  - If your tests aren’t repeatable in any environment, then you’ll always have an excuse for why they fail. 
  - You’ll also find yourself unable to run the tests when the environment isn’t available.


- **Self-Validating:** 
  - The tests should have a boolean output. 
  - Either they pass or fail. 
  - You should not have to read through a log file to tell whether the tests pass. 
  - You should not have
  to manually compare two different text files to see whether the tests pass. 
  - If the tests aren’t self-validating, then failure can become subjective and running the tests can require a long
  manual evaluation.


- **Timely:** 
  - The tests need to be written in a timely fashion. 
  - Unit tests should be written just before the production code that makes them pass. 
  - If you write tests after the production code, then you may find the production code to be hard to test. 
  - You may decide that some production code is too hard to test. 
  - You may not design the production code to be testable.