# Reflections

## Module 5

### Jmeter GUI /all-student-name

![image](https://github.com/Sirered/exercise-profiling/assets/126568984/6476c8ce-fe22-42d6-b8cb-388a90ab4551)

### Jmeter GUI /highest-gpa

![image](https://github.com/Sirered/exercise-profiling/assets/126568984/5058963a-cc49-4f85-b674-a976982639f1)

### Jmeter CLI /all-student-name

![image](https://github.com/Sirered/exercise-profiling/assets/126568984/f549a3c8-239f-46d0-a3ce-970cd0d2cb2a)

### Jmeter CLI /highest-gpa

![image](https://github.com/Sirered/exercise-profiling/assets/126568984/b3b91e02-78e4-448a-80bb-a19033b04585)

### Jmeter after refactoring /all-student-name

![image](https://github.com/Sirered/exercise-profiling/assets/126568984/68c2de77-d5dd-45aa-b1ae-f1977498127c)

### Jmeter after refactoring /highest-gpa

![image](https://github.com/Sirered/exercise-profiling/assets/126568984/3dcd382c-8409-4f32-abee-b0a4c5370c88)

**The differences from before and after**

Here we see that the time taken to fetch the data for both end points has since decreased drastically. For the \all-student and \highest-gpa endpoints I used JPARepository to my advantage, as I can use methods that would fetch all the student data and get the highest gpa in one method, requiring only one method call, rather than iterating through the massive tables in the database. For the \all-student-name endpoint, I just used striingbuilder which is mutable and easily changed, rather than concatenating string, which requires more time to rebuild the string as strings are immutabl

**What is the difference between the approach of performance testing with JMeter and profiling with IntelliJ Profiler in the context of optimizing application performance?**

JMeter allows us to simulate multiple users accessing the website at a single time, giving back information such as response time and throughput. This useful to see note the performance of your website when under the stress of multiple users in different scenarios in only one click of a button (the run test plan button). This allows for easy testing to see if there are any improvements regarding performance under specified conditions, after refactoring. On the other hand profiling will identify which method(s) are incurring the most load/taking the most time to be executed during the running of the program. This allows us to identify where we must focus on improving/refactoring to ensure our website runs as smoothly as possible. Overall JMeter is an excellent tool to **easily** test performance of a website or API without having to spend much time and resources to do so, while profiling should be done after JMeter notices issues in performance and will allow you to identify bottlenecks in your code that is causing those issues. 

**How does the profiling process help you in identifying and understanding the weak points in your application?**

Firstly, it identifies problem areas/methods in the code, by noting down the load and time taken by each method during the profiling. This will allow you to make more focused efforts when trying to improve the smoothness of the application.

Secondly it keeps track of the method call stack, which may be helpful if you wish to understand the basic flow of your application on build or when an endpoint is accessed, by having it shown in the flame graph. This is helpful when working with unfamiliar packages or APIs, especially if you are new to the project that you are currently working on, so you wouldn't know how some features are done.

Thirdly, if you store the results of your profiling everytime, which Intellij does do for you, you are able to see how much a method has improved from before and after the refactor. This facilitates iterative improvements, where you slowly make simple improvements step by step, witnessing what does and doesn't work, until you finally improved the method as much as possible (or at the very least enough to where it is not a hindrance). This type of approach is a lot more favourable compared to one giant overhaul, because making drastic changes is a good way to introduce unforeseen bugs and pointless or overengineered code(those that do very little to improve performance and may affect readability).

**Do you think IntelliJ Profiler is effective in assisting you to analyze and identify bottlenecks in your application code?**

I think it does, mostly because there isn't really any other tool that we have been taught that helps track the load created by each and every method or line of code. Unit and functional tests only eally tests if the code is correct. Jmeter will just tell you the overall performance of the program when running a certain scenario. Profiler will actually tell you the information regarding each and every method call run during the profiling and will show and warn you of these potential bottlenecks. I do wish that the profiler was easier to use (for example when using SpringBoot, it is very difficult to find the methods that I made among the various methods that are called that are part of SpringBoot, Java or any other packages). Fortunately, methods, as well as lines that take a while to run, have the amount of time for it to run on the left, helpfully colour coded according to how bad it is, so if I already have a method in mind, it is easy to see to what extent it is a bottleneck.

**What are the main challenges you face when conducting performance testing and profiling, and how do you overcome these challenges?**

In regards to Jmeter the main issue is that I'm still not accustomed to using it and understanding all of the features available. So far all I can do is test the ability to access an endpoint with a bunch of users. I don't know how to emulate putting input (which I bet is something you can do with Jmeter), I don't know how to read some of the Samplers properly other than the summary table, I don't know how to make them access more than one endpoint during a test. All I can do right now is make them access a GET end point with no authentication and authorisation and see how fast fetching data is for them. In the future, when dealing with more complex test scenarios, I will have to learn more about Jmeter to more productively use Jmeter. 

As for profiling, as mentioned in the answer to the previous question, it really is a lot of information overload when you have a lot of other Springboot packages that weren't made by me and thus can't be optimised, filling the entire flame diagram and method list. I just need to get more used to Springboot's flow and just filtering out unrelated (stuff I can't really change) method calls to find what I'm actually looking for.

**What are the main benefits you gain from using IntelliJ Profiler for profiling your application code?**

Firstly, it is seemly integrated into the Intellij IDE, so I can let it profile, while I'm running the code and get instant feedback. I don't have to worry about having to somehow connect the profiler to whatever IDE I'm using, as Intellij profiler is part of the IDE I am using and is made to work with that IDE. All results are in a tab within that IDE, which although I have complained that it is difficult to navigate through, it is still helpful that I don't have to open a different window to find my results, plus after profiling it even shows some of the results within the code, which is very helpful for when you are focusing on a specific piece of code (here I'm mainly talking about the text telling how long the method was run during profiling next to where it is called). 

Secondly, Intellij Profiler offers many ways to view the methods ran during the profiling. I can view the flame graph to see what percentage of the load was due to what method. The method list is a lot easier to navigate when you are trying to find the 'worst' methods or a specific method, which is difficult to do in the flame graph. The timeline allows for a better visualisation of what method was called when. Due to this variety, it is easy to visualise the metric you are looking for.

Lastly, as it is part of IntelliJ, it is likely going to be updated at least semi-frequently along with all of Intellij's other tools, so if there is more work that profilers need to do in the future, or there is a popular feature that users what implemented, the Intellij Profiler will likely implement such eventually, keeping everything up to date, unlike some tools which after a while may not get anymore updates.

**How do you handle situations where the results from profiling with IntelliJ Profiler are not entirely consistent with findings from performance testing using JMeter?**

Firstly, I would check if all configurations and testing conditions are the same if not similar. For example, it wouldn't be right if the profiling was done on a different day, or using a different server, or using a different controller, as those may cause differences in testing.

If all configurations and all testing conditiomns are indeed similar, there must be something wrong with the Jmeter test plan. I think this, because as far as I know, to use the profiler, you have to manually access the website similar to a user, whereas the Jmeter tests are automatic and may not correctly imitate how a user may interact with the website. In which case you need to make sure that your tests are correct and up to date. For example you should check if the end points used are the same, it may be the case that the Jmeter is still using the old endpoint with the unoptimised code, but when you tested it, you used the new and faster end point. If there is a way to automate profiling into tests, then both the profiling test suite and the Jmeter test plan should be compared and be updated to be similar to each other and how users will actually use the website. Overall, if there is a discrepancy, there is likely something wrong with the test plan, in which case they should be analysed and updated accordingly.

**What strategies do you implement in optimizing application code after analyzing results from performance testing and profiling? How do you ensure the changes you make do not affect the application's functionality?**

First, I would remind myself of data structures and algorithms that may have better time and/or space complexity compared to the current implementation, and implement such. If I can't think of any by myself, I'll consult google, forums like stackoverflow, youtube videos and AI such as chatgpt, to see if someone else needed to make similar optimisations, and how they did it. If there is no easy fix I would or implementation that works with my current project structure, I would have to think about refactoring other parts of my code to be able to utilise more optimal methods.

To ensure that it does not affect application functionality, I need to have unit tests to test the methods. It can be tests from TDD flow, or not, at the very least the tests were made, are valid, and were all passed by the program before any refactorisation is done. After refactorisation we would run the same test suite and see if it still all passes. If it doesn't we would have to inspect the scenario that it failed at and refactor the program (or possibly the tests if they were too coupled with the method of implementation) until it all passes again.
