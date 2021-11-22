
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

