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

Secondly it keeps track of the method call stack, which may be helpful if you wish to understand the basic flow of your application on build or when an entrypoint is accessed, by having it shown in the flame graph. This is helpful when working with unfamiliar packages or APIs, especially if you are new to the project that you are currently working on, so you wouldn't know how some features are done.

Thirdly, it seems that Intellij keeps track of previous profiling, so you are able to see how much a method has improved from before and after the refactor. This facilitates iterative improvements, where you slowly make simple improvements step by step, witnessing what does and doesn't work, until you finally improved the method as much as possible (or at the very least enough to where it is not a hindrance). This type of approach is a lot more favourable compared to one giant overhaul, because making drastic changes is a good way to introduce unforeseen bugs and pointless or overengineered code(those that do very little to improve performance and may affect readability).

**Do you think IntelliJ Profiler is effective in assisting you to analyze and identify bottlenecks in your application code?**

I think it does, mostly because there isn't really any other tool that we have been taught that helps track the load created by each and every method or line of code. Unit and functional tests only eally tests if the code is correct. Jmeter will just tell you the overall performance of the program when running a certain scenario. Profiler will actually tell you the information regarding each and every method call run during the profiling and will show and warn you of these potential bottlenecks. I do wish that the profiler was easier to use (for example when using SpringBoot, it is very difficult to find the methods that I made among the various methods that are called that are part of SpringBoot, Java or any other packages). Fortunately, methods, as well as lines that take a while to run, have the amount of time for it to run on the left, helpfully colour coded according to how bad it is, so if I already have a method in mind, it is easy to see to what extent it is a bottleneck.

