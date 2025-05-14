<style>

body {
    counter-reset: h2counter;
}

/* H1 - No numbering */
h1 {
    /* No counter reset or increment */
}

/* H2 - Level 1 numbering */
h2 {
    counter-reset: h3counter;
}

h2::before {
    counter-increment: h2counter;
    content: counter(h2counter) ". ";
}

/* H3 - Level 2 numbering */
h3 {
    counter-reset: h4counter;
}

h3::before {
    counter-increment: h3counter;
    content: counter(h2counter) "." counter(h3counter) " ";
}

/* H4 - Level 3 numbering (optional) */
h4 {
    counter-reset: h5counter;
}

h4::before {
    counter-increment: h4counter;
    content: counter(h2counter) "." counter(h3counter) "." counter(h4counter) " ";
}

</style>

# Evidence and Knowledge

This document includes instructions and knowledge questions that must be completed to receive a *Competent* grade on this portfolio task.

## Required evidence

### Answer all questions in this document

- Each answer should be complete, well-articulated, and within the specified word count limits (if added) for each question.
- Please make sure **all** external sources are properly cited.
- You must **use your own words**. Please include your full chat transcripts if you use generative AI in any way.
- Generative AI hallucinates, is not an authoritative source

### Make all the required modifications to the code

- Please follow the instructions in this document to make the changes needed to the code.

- When requested to upload evidence, upload all screenshots to `screenshots/` and embed them in this document. For example:

```markdown
![Example Running Code](screenshots/screenshot1.png)
```

- You must upload the code into your GitHub repository.
- While you can use a branch, your code should be in main when you submit.
- Upload a zip of this repository to Blackboard when you are ready to submit.
- You will be notified of your result via Blackboard
- However, if using GitHub classrooms, you may also receive additional feedback on GitHub directly

### Optional: Use of Raspberry Pi and SenseHat

Raspberry Pi or SenseHat is **optional** for this activity. You can use the included `sense_hat.py` file to simulate the SenseHat on your computer.

If you use a Pi, please **delete** the `sense_hat.py` file.

### Accessible version of the code

This project relies on visual patterns that appear on an LED matrix. If you have any accessibility requirements, you can use the `udl/accessible` branch to complete the project. This branch provides an accessible code version that uses text-based patterns instead of visual ones.

Please discuss this with your lecturer before using that branch.

## Specific Tasks & Questions

Address the following tasks and questions based on the code provided in this repository.

### Set up the project locally

1. Fork this repository (if not using GitHub Classrooms)
2. Clone your repository locally
3. Run the project locally by executing the `main.py` file
4. Evidence this by providing screenshots of the project directory structure and the output of the `main.py` file

![Local Execution (INSERT YOUR SCREENSHOT)](screenshots/CREATE_A_SCREENSHOT_OF_YOUR_local_setup.png)
![](.\proj1.png "Pycharm Project Directory")
![](.\proj2.png "main.py Output")
If you are running on a Raspberry Pi, you can use the following command to run the project and then screenshot the result:

```bash
ls
python3 main.py
```

### Fundamental code comprehension

 Answer each of the following questions **as they relate to that code** supplied by in this repository (ignore `sense_hat.py`):

1. Examine the code for the `smiley.py` file and provide  an example of a variable of each of the following types and their corresponding values (`_` should be replaced with the appropriate values):

   | Type                    | name  | value                |
   | ----------              |-------|----------------------|
   | built-in primitive type | dimmed| True                 |
   | built-in composite type | YELLOW | (255, 255, 0)        |
   | user-defined type       |self.sense_hat.low_light| dimmed which is True |

2. Fill in (`_`) the following table based on the code in `smiley.py`:

   | Object                   | Type                      |
   | ------------             |---------------------------|
   | self.pixels              | list                      |
   | A member of self.pixels  | tuple                     |
   | self                     | <class '__main__.smiley'> |

3. Examine the code for `smiley.py`, `sad.py`, and `happy.py`. Give an example of each of the following control structures using an example from **each** of these files. Include the first line and the line range:

   | Control Flow | File     | First line | Line range |
   | ------------ |----------|------------|------------|
   |  sequence    | sad.py   | 15         | 15         |
   |  selection   | sad.py   | 26         | 26 - 29    |
   |  iteration   | happy.py | 21         | 21 - 22    |

4. Though everything in Python is an object, it is sometimes said to have four "primitive" types. Examining the three files `smiley.py`, `sad.py`, and `happy.py`, identify which of the following types are used in any of these files, and give an example of each (use an example from the code, if applicable, otherwise provide an example of your own):

   | Type                    | Used? | Example                                                     |
   | ----------------------- |-------|-------------------------------------------------------------|
   | int                     | yes   | for pixel in eyes: (line 25 in sad.py where pixel is a int) |
   | float                   | yes   | delay=0.25 (line 33 in happy.py)                            |
   | str                     | No    | string_name = "Hello"                                       |
   | bool                    | yes   | wide_open=True (line 19 in sad.py)                          |

5. Examining `smiley.py`, provide an example of a class variable and an instance variable (attribute). Explain **why** one is defined as a class variable and the other as an instance variable.

> Class variable - WHITE.
> Instance variable - self.pixels.
>WHITE is a static fixed value which does not need to change with each instance hence it can be defined once and does not need to be saved multiple times for each instance. Pixels is an instance variable as its items values (which make up the mock sensehat LED screen) can be changed for each instance based on display requirements. 

6. Examine `happy.py`, and identify the constructor (initializer) for the `Happy` class:
   1. What is the purpose of a constructor (in general) and this one (in particular)?

   >In happy.py, the constructor is on line 10 - 14. A constructor in general initializes the attributes of an object each time an instance of a class is created. In happy.py, the constructor initializes an instance of Happy class which includes inheritance of all attributes from 2 parent classes (Smiley and Blinkable) and calls two methods (draw_mouth which renders a mouth and draw_eyes which draws eyes on a standard smiley).
   >

   2. What statement(s) does it execute (consider the `super` call), and what is the result?

   >  It runs init from Smiley class which runs SenseHat() method, sets attribute Y to yellow and O to black colour for the instance and sets pixels list to a default set of Y and O attribute values. If Bliankable class had an init this would also be run for this instance. The init statements also call 2 methods draw_mouth (which renders a mouth and draw_eyes which draws eyes on a standard smiley).
   >

### Code style

1. What code style is used in the code? Is it likely to be the same as the code style used in the SenseHat? Give to reasons as to why/why not:
   
> OOP (Object-Oriented Programming). SenseHat follows a similar modular programming style with the call of functions. Furthermore, the workings of SenseHat is encapsulated. Both indicative that SenseHat is likely to on the guidelines of OOP. 
>

2. List three aspects of this convention you see applied in the code.

> Inheritance, Encapsulation, Polymorphism
>

3. Give two examples of organizational documentation in the code.

> Comments (main.py), docstrings (main.py, sad.py, happy.py, smiley.py, blinkable.py)
>

### Identifying and understanding classes

> Note: Ignore the `sense_hat.py` file when answering the questions below

1. List all the classes you identified in the project. Indicate which classes are base classes and which are subclasses. For subclasses, identify all direct base classes.
  
  Use the following table for your answers:

| Class Name | Super or Sub? | Direct parent(s)  |
|------------|---------------|-------------------|
| Happy      | Sub           | Smiley, Blinkable |
| Sad        | Sub           | Smiley            |
| Blinkable  | Super         |                   |
| Smiley     | Super         |                   |

2. Explain the concept of abstraction, giving an example from the project (note "implementing an ABC" is **not** in itself an example of abstraction). (Max 150 words)

> Abstraction is the process of including only essential information from a whole process in a class and omitting complex internal implementation details if they are not relevant to the current project. This class only forms a blueprint for other classes and cannot be initiated. It can contain abstract methods and interfaces. The specific task behaviours are defined in sub-class methods as required and not in the abstract class. The abc (Abstract Base Class) module is used to create abstract classes and interfaces where all methods specified in the abstract class as place holders need to have relevant code in the subclass which links to the abstract super class. 

>In happy.py, class Happy has a parent class Blinkable which has an abs class Blinkable and method blink() as a blueprint. Because of this, class Happy has to have a method called blink() with the code for the specific required behaviour.

3. What is the name of the process of deriving from base classes? What is its purpose in this project? (Max 150 words)

> Inheritance. In smiley.py, class Smiley is the base class and it defines the layout and base colours of the sensehat. Sad.py and happy.py have class Sad and class Happy respectively which inherit from class Smiley and help put emotions on the sensehat defined in class Smiley.py  
>

### Compare and contrast classes

Compare and contrast the classes Happy and Sad.

1. What is the key difference between the two classes?
   > Happy inherits from class Blinkable (an abstract class with an abstract method blink()) which is not included in the inheritance for Sad. Happy also has an additional method called blink() as required by the abstract class blinkable inheritance.
   >
2. What are the key similarities?
   > They both inherit from class Smiley. They both have methods called draw_mouth() and draw_eyes() (though with key differences in the functionality). 
   >They both change values in attribute pixels which is our sensehat (though different values to showcase different emotions).  
3. What difference stands out the most to you and why?
   > The inheritance to class Blinkable in class Happy and an additional method blink() which allows happy to have an increased number of emotions coded in methods (and hence functionality) on the sensehat (3 emotions / faces instead of the 2 possible with sad). 
   >
4. How does this difference affect the functionality of these classes
   > It allows Happy to have additional functionality (a blink emotion on the sensehat with a delay timer) with the inclusion of a blink() method from class Blinkable though with proprietary functioning stated in class Happy. 
   >

### Where is the Sense(Hat) in the code?

1. Which class(es) utilize the functionality of the SenseHat?
   > Smiley, Sad, Happy 
   >
2. Which of these classes directly interact with the SenseHat functionalities?
   > Smiley
   >
3. Discuss the hiding of the SenseHAT in terms of encapsulation (100-200 Words)
   > The workings of SenseHat is obscured and not available to the coder. It's properties and behaviours are clearly defined allowing for reuse of code. The coder cannot erroneously make changes to the working of SenseHat ie it is protected.SenseHat has a predetermined set of attributes and behaviours which can be accessed in a controlled manner. These all highlight the encapsulated nature of SenseHat.
   > Encapsulation is a technique for hiding a class's internal operations and exposing only the information required for external interactions. It enables the creation of objects with clearly defined behaviours and properties, enhancing their usability and security. Encapsulation restricts access to a class's code, it's methods and keeps it's variables private.  
   >

### Sad Smileys Can’t Blink (Or Can They?)

Unlike the `Happy` smiley, the current implementation of the `Sad` smiley does not possess the ability to blink. Let's first explore how blinking has been implemented in the Happy Smiley by examining the blink() method, which takes one argument that determines the duration of the blink.

**Understanding Blink Mechanism:**

1. Does the code's author believe that every `Smiley` should be able to blink? Explain.

> Currently, the coder has incorporated a blink() module for the Happy class only (meaning that only a happy smiley has a blink option) and not for the Sad class. Some smileys can be changed to enable blink such as sad. However, blink may not apply for all emotions (example angry where angry people usually do not blink). 
>

2. For those smileys that blink, does the author expect them to blink in the same way? Explain.

> Not necessarily. A sad emotion for example may have the eyes closed in a blink for a longer duration than a happy smiley.  
>

3. Referring to the implementation of blink in the Happy and Sad Smiley classes, give a brief explanation of what polymorphism is.

> Polymorphism occurs when 2 or more classes have the same behaviour type ie method name but the behaviours morph into specific individual behaviours for each of the classes. In the case of Happy and Sad classes, both could have a method named blink but the blink method for each of these classes could behave quite differently (example Sad blink could have eyes closed for a longer duration then Happy blink).     
>

4. How is inheritance used in the blink method, and why is it important for polymorphism?

> Sad and Happy classes have Blinkable as the parent class with the method blink in it as an abstract method (once Sad is set-up with blink method). Both classes have individual blink methods set-up for each class's individual requirements. Inheritance is important for polymorphism because it provides the hierarchy structure which states which method calls are common to base and child classes. 
>
1. **Implement Blink in Sad Class:**

   - Create a new method called `blink` within the Sad class. Ensure you use the same method signature as in the Happy class:

   ```python
   def blink(self, delay=0.25):
       pass  # Replace 'pass' with your implementation
   ```

2. **Code Implementation:** Implement the code that allows the Sad smiley to blink. Use the implementation from the Happy Smiley as a reference. Ensure your new method functions similarly by controlling the blink duration through the `delay` argument.

3. **Testing the Implementation:**

- Test the new blink functionality on your Raspberry Pi or within the Python classes provided. You might need to adjust the `main.py` script to incorporate Sad Smiley's new blinking capability.

Include a screenshot of the sad smiley or the modified `main.py`:
![](.\proj3.png "screenshot of amended main.py")
![](.\proj4.png "Screenshot of blink() module in sad.py")
![](.\proj5.png "Sad smiley run")
![Sad Smiley Blinking](screenshots/sad_blinking.png)

- Observe and document the Sad smiley as it blinks its eyes. Describe any adjustments or issues encountered during implementation.

  > Sad class needed to be imported in main.py before Sad() could be called. In sad.py, time needed to be imported (for delay functionality) and blinkable from Blinkable. 

  ### If It Walks Like a Duck…

  Previously, you implemented the blink functionality for the Sad smiley without utilizing the class `Blinkable`. Assuming you did not use `Blinkable` (even if you actually did), consider how the Sad smiley could blink similarly to the Happy smiley without this specific class.

  1. **Class Type Analysis:** What kind of class is `Blinkable`? Inspect its superclass for clues about its classification.

     > abstract class 

  2. **Class Implementation:** `Blinkable` is a class intended to be implemented by other classes. What generic term describes this kind of class, which is designed for implementation by others? **Clue**: Notice the lack of any concrete implementation and the naming convention.

  > Your answer here

  3. **OO Principle Identification:** Regarding your answer to question (2), which Object-Oriented (OO) principle does this represent? Choose from the following and justify your answer in 1-2 sentences: Abstraction, Polymorphism, Inheritance, Encapsulation.

  > Your answer here

  4. **Implementation Flexibility:** Explain why you could grant the Sad Smiley a blinking feature similar to the Happy Smiley's implementation, even without directly using `Blinkable`.

  > I could do this by adding a new module in class Sad for the blink functionality.  

  5. **Concept and Language Specificity:** In relation to your response to question (4), what is this capability known as, and why is it feasible in Python and many other dynamically typed languages but not in most statically typed programming languages like C#? **Clue** This concept is hinted at in the title of this section.

  > Duck typing. In Python and other dynamically typed languages, the type of an object is less important than the method it defines and it is not required to specifically set a type at the onset. A type can also change within the running of code as required. Statistically, typed programming follows a more rigid framework where often each module / variable etc. has to be pre-defined and the type specified. 

  ***

  ## Refactoring

  ### Does a Smiley Have to Be Yellow?

  While our current implementation predominantly features yellow smileys, emotional expressions like sickness or anger typically utilize colors like green, red, or orange. We'll explore the feasibility of integrating these colors into our smileys.

  1. **Defined Colors and Their Location:**

     1. Which colors are defined and in which class(s)?
        > The colours are defined in class Smiley. The colours currently defined are white, green, red, yellow and black.
     2. What type of variables hold these colors? Are the values expected to change during the program's execution? Explain your answer.
        > Type is Tuple. At the moment the values do not change within the code.
     3. Add the color blue to the appropriate class using the appropriate format and values.

  2. **Usage of Color Variables:**

     1. In which classes are the color variables used?
        > Sad, Happy, Smiley

  3. **Simple Method to Change Colors:**
  4. What is the easiest way you can think to change the smileys to green? Easiest, not necessarily the best!
     > Set variable Y to Green in class Smiley __init__ (currently Y is set to Yellow)

  Here's a revised version of the "Flexible Colors – Step 1" section for the smiley project, incorporating your specifications for formatting and content updates:

  ### Flexible Colors – Step 1

  Changing the color of the smileys once is straightforward, but it isn't very flexible. To facilitate various colors for smileys, it is advisable not to hardcode values in any class. This approach was identified earlier as a necessary change. Let's start by removing the built-in assumptions about color in our classes.

  1. **Add a method called `complexion` to the `Smiley` class:** Implement this instance method to return `self.YELLOW`. Using the term "complexion" instead of "color" provides a more abstract terminology that focuses on the meaning rather than implementation.

  2. **Refactor subclasses to use the `complexion` method:** Modify any subclass that directly accesses the color variable to instead utilize the new `complexion` method. This ensures that color handling is centralized and can be easily modified in the future.

  3. **Determine the applicable Object-Oriented principle:** Consider whether Abstraction, Polymorphism, Inheritance, or Encapsulation best applies to the modifications made in this step.

  4. **Verify the implementation:** Ensure that the modifications function as expected. The smileys should still display in yellow, confirming that the new method correctly replaces the direct color references.

  This step is crucial for setting up a more flexible system for color management in the smiley display logic, allowing for easy adjustments and extensions in the future.

  ### Flexible Colors – Step 2

  Having removed the hardcoded color values, we now enhance the base class to support dynamic color assignments more effectively.

  1. **Modify the `__init__()` method in the `Smiley` class:** Introduce a default argument named `complexion` and assign `YELLOW` as its default value. This allows the instantiation of smileys with customizable colors.

  2. **Introduce a new instance variable:** Create a variable called `my_complexion` and assign the `complexion` parameter to it. This step ensures that each smiley instance can maintain its own color state.

  3. **Rationale for `my_complexion`:** Using a distinct instance variable like `my_complexion` avoids potential conflicts with the method parameter names and clarifies that it is an attribute specific to the object.

  4. **Bulk rename:** We want to update our grid to use the value of complexion, but we have so many `Y`'s in the grid. Use your IDE's refactoring tool to rename all instances of the **symbol** `Y` to `X`. Where `X` is the value of the `complexion` variable. Include a screenshot evidencing you have found the correct refactor tool and the changes made.
![](.\proj7.png "Refractor Y to X")
![](.\proj6.png "Y successfully refractored to X")
![](.\proj8.png "X variable = complexion")
  5. ![Bulk Rename](screenshots/bulk_rename.png)

  5. **Update the `complexion` method:** Adjust this method to return `self.my_complexion`, ensuring that whatever color is assigned during instantiation is what the smiley displays.

  6. **Verification:** Run the updated code to confirm that Smileys still defaults to yellow unless specified otherwise.

  ### Flexible Colors – Step 3

  With the foundational changes in place, it's now possible to implement varied smiley colors for different emotional expressions.

  1. **Adjust the `Sad` class initialization:** In the `Sad` class's initializer method, change the superclass call to include the `complexion` argument with the value `self.BLUE`, as shown:

     ```python
     super().__init__(complexion=self.BLUE)
     ```

  2. **Test color functionality for the Sad smiley:** Execute the program to verify that the Sad smiley now appears blue.

  3. **Ensure the Happy smiley remains yellow:** Confirm that changes to the Sad smiley do not affect the default color of the Happy smiley, which should still display in yellow.

  4. **Design and Implement An Angry Smiley:** Create an Angry smiley class that inherits from the `Smiley` class. Set the color of the Angry smiley to red by passing `self.RED` as the `complexion` argument in the superclass call.

  ***
