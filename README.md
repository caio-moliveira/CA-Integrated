# CA - Artificial Intelligence and Data Visualization
 



 









Subject: Artificial Intelligence
&
Data Visualization and Communication


Lecturer: David McQuaid
&
Sam Weiss






Caio Machado de Oliveira
ID: 2020351










 January/2024


Declaration 
			
By submitting this assessment, I confirm that I have read the CCT policy on Academic Misconduct and understand the implications of submitting work that is not my own or does not appropriately reference material taken from a third party or other sources. I declare it to be my work and that all material from third parties has been appropriately referenced. I further confirm that this work has not previously been submitted for assessment by myself or someone else in CCT College Dublin or any other higher education institution.































 
## Artificial Intelligence

#### Using any CSP (Constraint Satisfaction Problem) framework (using variables, value domains, and constraints), discover if the above problems can be solved and if so detail who would be hired
#### Scenario 1: 

Suppose Ciara knows Python, and only has funds to hire three more people.

Variables: The variables are the people (Peter, Juan, Jim, Jane, Mary, Bruce, Anita). Each person represents a variable that needs to be assigned a role based on their abilities.

Value Domains: The domain of each variable (person) is their set of abilities. For example, the domain for Peter is {"Python", "AI"}.

Constraints: Each person can be assigned only to roles matching their abilities.

The total number of people hired should be three (excluding Ciara).

The required roles in the company ('constraints') must all be filled. This includes 1 Python Programmer, 2 AI Engineers, 1 Web Designer, 1 Database Admin, and 1 Systems Engineer.

#### Scenario 2:

Suppose Ciara and Juan become partners, with the additional funds they can now employ four more people but must employ another AI Engineer, so they need 2 Python Programmers, 3 AI Engineers, 1 Web Designer, 1 Database Admin, and 1 Systems Engineer.
Variables and Value Domains remains the same as scenario 1.
Constraints:
Juan becomes Ciara's partner and will be moved to pre-selected list.
The total number of people hired must be up to four (excluding Ciara and Juan)
The required roles in the company constraint must all be filled. This includes 2 Python Programmer, 3 AI Engineers, 1 Web Designer, 1 Database Admin, and 1 Systems Engineer.


#### Code Explanation

- `variables_domain`:  A string dictionary where the skills are assigned to each person accordingly. 

- `constraint`: A dictionary representing the required skills or roles for the project. Each skill has a corresponding number indicating how many people with that skill are needed.

- `pre_selected`: A set of individuals who are pre-selected for the team due to their specific skills or other constraints. For instance, in scenario 1, Ciara is selected for her Python skill. For instance, in scenario 2, Ciara and Juan are selected for their skills. It adjusts the variables_domain and `constraint` based on the skills of these pre-selected individuals.

Removing pre-selected individuals: A for loop to remove the pre-selected individuals from the variables_domain and adjusts the constraint accordingly to reflect their contribution to the required skills.

- `meets_requirements`: A function that checks if a particular combination of people meets the required skills. It tallies the skills of the combination and compares this against the constraint to determine if it's a valid team setup.

##### Process:

* Initialize a count for each required skill.
* Tally the skills for each individual in the combination.
* Compare the tally against the requirements in constraint.

Generating Possible Teams: The possible_teams generates all combinations (for scenario 1) of 1 to 4 people from the remaining candidates and (for scenario 2) of 1 to 6 people from the remaining candidates (not including pre-selected ones) and checks each combination to see if it meets the required skills.

Valid combinations that meet all constraints are stored in possible_teams, each including the pre-selected individuals then stores each team combination that successfully meet all the constraints.

### Discuss in detail how using Constraint Satisfaction finds an answer or finds no solution to the problems in Tasks for Artificial Intelligence part 1. How does this differ from standard algorithmic solutions?

#### Constraint Satisfaction Problem (CSP)

A Constraint Satisfaction Problem (CSP) involves finding a solution that satisfies a number of constraints or conditions. It is widely used in fields like artificial intelligence for scheduling, assigning, and planning problems. CSPs typically involve variables, domains for each variable, and constraints that describe allowable combinations of values. The goal is to assign values to all variables in a way that doesn't violate any constraints (Russell & Norvig, 2010). This framework is particularly effective in scenarios like employee scheduling, where multiple conditions must be met simultaneously.

A Constraint Satisfaction Problem (CSP) is typically defined by three fundamental components: (Wikipedia Contributors, 2019)

![image](https://github.com/caio-moliveira/CA-Integrated/assets/150807759/8224a6b7-a9a6-49ee-8103-6740703315cc)

 
A more efficient method uses the backtracking paradigm (BT) that is the most common algorithm for performing systematic search. Backtracking incrementally attempts to extend a partial solution toward a complete solution, by repeatedly choosing a value for another variable.

The backtracking paradigm carefully builds a solution to a problem by testing using many options and discarding those that don't work. It attempts to gradually expand the partial solution that it begins with. It selects a variable and gives it a consistent value at each step, while at the same time ensuring that the current sequence of assignments doesn't violate any constraints. If a constraint is violated, the algorithm doesn't proceed further down that path and instead goes back (or "backtracks") to the previous step to try a different value or path. (Barták, Morris, & Venable, 2014)

A common issue with most backtracking-based systematic search algorithms is that there are a lot of "backtracks" to other options, which reduces system efficiency. There are specific situations where it is feasible to fully remove the necessity for going back. Additionally, there are methods that select a unique variable ordering to minimize the amount of backtracking.

Variables (X):
- Each potential person: Peter, Juan, Jim, Jane, Mary, Bruce, Anita and Ciara).
- Each variable can take on values from a domain.

Domains (D):
- Each domain is a set of possible values that its corresponding variable can assume. In this case, the abilities each person (Variables) has.
- Domains can be finite or infinite, depending on the specific CSP.

Constraints (C):
- Each constraint involves some subset of the variables and specifies the allowable combinations of values those variables can take. Constraints can be represented in various ways, including explicit lists of allowable combinations or more general mathematical relations or logical propositions.

Scenario 1:
1. There must be 2 Python Programmers, 2 AI Engineers, 1 Web Designer, 1 Database Admin, and 1 Systems Engineer;
2. Ciara knows Python, so 1 Python role is taken (remaining 1);
3. The company can hire only 3 people to fill the rest of the roles.









The following graphs were taken from the code itself:

![image](https://github.com/caio-moliveira/CA-Integrated/assets/150807759/0cc8e7a3-858c-4e9a-ba9b-eb5eab785ff2)


  
Result: Two possible teams have been found.
- Ciara, Jane, Jim, Juan
- Anita, Ciara, Jane, Jim

Scenario 2:
1. There must be 2 Python Programmers, 3 AI Engineers, 1 Web Designer, 1 Database Admin, and 1 Systems Engineer;
2. This time, Juan and Ciara have to be on the list of hired people with their respective abilities.
3. The company can hire max of 4 people for the rest of the roles.

![image](https://github.com/caio-moliveira/CA-Integrated/assets/150807759/682c568e-af8f-4e10-8733-5b3f8672ae43)



Result: nine possible teams have been found.

- Anita, Ciara, Jane, Jim, Juan
- Ciara, Jane, Jim, Juan, Peter
- Anita, Ciara, Jane, Jim, Juan, Mary
- Anita, Ciara, Jane, Juan, Mary, Peter
- Ciara, Jane, Jim, Juan, Mary, Peter
- Anita, Ciara, Jane, Jim, Juan, Peter
- Anita, Bruce, Ciara, Jane, Jim, Juan
- Anita, Bruce, Ciara, Jane, Juan, Peter
- Bruce, Ciara, Jane, Jim, Juan, Peter

Objective:
The objective of a CSP is to find an assignment of values to variables that satisfies all constraints.

Solution:
The CSP algorithm would try different combinations of the candidates, assigning them to various roles while ensuring all constraints are met.

A solution to the CSP is an assignment of values to all variables that does not violate any constraints. Depending on the problem, there might be none, one, or many possible solutions.

It uses backtracking to explore all possible configurations going backwards and checking if any constraint is violated.

Scenario 1 found only two solutions. The reason is that only 3 people were hired to fulfill 6 roles, making the constraints harder to satisfy.

Scenario 2 found close to ten solutions. The reason is that Juan is now Ciara's partner, and both must be part of the hired team. Now, the constraints are much easier to satisfy, as there are 5 abilities left to be distributed among 4 people.

### Conclusion

Most algorithms for solving CSPs search systematically through the possible assignments of values to variables. These algorithms are going to find a solution, if one exists, or to prove that the problem is unsatisfiable. (Brailsford, Potts & Smith, 1999)
CSPs are a powerful abstract model for representing and solving many real-world problems in various fields such as scheduling, planning, resource allocation, configuration, and spatial reasoning. They offer a structured way to break down complex problems into manageable components (variables, domains, and constraints) and apply systematic methods to find solutions.
	










## These problems be solved using several other algorithm’s we have studied in the module. Choose one of these algorithms and discuss your answer in detail including a proof of your hypothesis in code
### Integer Linear Programming (ILP)

Integer Linear Programming (ILP) is a type of mathematical optimization or feasibility program used to find the best solution out of a set of possible solutions. In ILP:
• Variables are restricted to be integers.
• The objective is often to minimize or maximize some linear function of those integers.

The assumption of divisibility, which limits decision variables to noninteger values, is the main drawback of linear programming. However, in several real-world situations, decision variables need to have integer values such as assigning people, machines, or vehicles to activities. (Hillier & Lieberman, 2010)

The ILP algorithm finds every feasible unique solution by use of a unique twist on iterative integer linear programming: solution blocking. It uses integer constraints (binary variables for assignments and hiring) along with linear programming techniques for optimization (minimizing the number of hired people), and iteratively adds constraints to fully explore the solution space. When addressing issues involving resource allocation and operations research, where specific goals must be optimized within predetermined parameters, this kind of problem-solving is most prevalent.

### How ILP Works

Variable Definition: A decision point is represented by each variable. For instance, a variable may indicate whether a person is assigned to a specific job in a resource allocation problem (1 for yes, 0 for no).

Constraints: Setting requirements that all solutions must adhere to is necessary for ILP. These can ensure that resources aren't over-allocated, and that only feasible solutions are considered. Typical restrictions include making sure the right number of roles are filled or that no one is put in a role that isn't a good fit for them based on their abilities.

Objective Function: What you want to optimize is the objective function, which might be anything like maximizing efficiency or lowering expenses. Sometimes, the goal could be as simple as identifying any feasible solution that satisfies the constraints.

#### Advantages of ILP
• Optimality: ILP can provide the best possible solution according to the objective function and within the constraints.
• Flexibility: It can deal with a broad range of problem types, including complex and large-scale problems.
• Universality: ILP models are broadly applicable in numerous fields such as scheduling, resource allocation, budgeting, etc. (Hillier & Lieberman, 2010)

### Conclusion
The inconsistency of Integer Linear Programming (ILP) algorithms in solving integer problems represents a notable drawback. While theoretical demonstrations assert these algorithms' convergence within a finite number of iterations, practical implementation on computers can yield a different experience. As such, it's important to consider these computational limitations and the potential for inconsistency when examining and applying ILP algorithms. (Taha, 2017).


### Code Explanation

Uses the `LpProblem` with an objective to minimize (`LpMinimize`) the number of people on each team ensuring all constraints are filled.
`X` stores a binary value to indicate which person is assigned to the roles accordingly.
`Hired` is also a binary variable that will store whether the person is on the team.
It defines the objective of the code by minimizing the number of people hired until get all the possible solutions
Def `block_previous_solutions` keeps solving the problem until finds all solutions without repeating the answer.


















## Data Visualization & Communication

### Include in your report a section for a theoretical AI “team” you are part of, explaining the visualisation processes and rationalising your visualisation decisions (eg chart choice, colour, layout etc).

Effective use of numbers in communication is critical in today's data-driven environment. In "Storytelling with Data," Cole Nussbaumer Knaflic makes the following claim: "Numbers have an important story to tell. They rely on you to give them a clear and convincing voice" (Knaflic, 2015). Our goal is to turn raw data into fascinating stories by carefully choosing charts, selecting color palettes, and developing layout designs. The concepts of clarity, understanding, and engagement inform our visualization selections, guiding us in making sure that every graph and chart has a purpose and contributes to the overall story. As we examine the facts, let's keep in mind the narrative's ability to transform meaningless statistics into insightful understandings.

#### Visualization Process and Rational 

In order to clarify the results and highlight possible solutions, we have utilized two different bar graphs, each of which has a specific function inside our story.

#### Graph 1: Selected People Frequency

The first graph uses a bar chart, with the names of the individuals shown on the x-axis and the number of times each individual was chosen to be a member of a team quantified on the y-axis.
Stakeholders may rapidly identify the most desirable candidates for team creation according to this depiction. We personalize the data by utilizing individual names on the x-axis, which makes it simpler to discuss and more relatable. Here, a bar graph is purposefully used to emphasize candidates that are regularly selected and may be viewed as major participants. Its simple structure allows for quick comparisons among applicants.






#### Graph 2: Team size Frequency

In the second graph, we have also a bar chart where the y-axis shows the number of teams that fit into each size group and the x-axis shows the different team sizes that we saw in our data.
This graph shows popular or ideal team sizes and offers insights into the most typical team setups. By selecting a bar graph, the emphasis is kept on the size of team occurrences, which facilitates quick comparisons of various team size frequencies. This graphic aids in comprehending the distribution of team sizes and may assist determine the appropriate team size in different situations.


### Create interactive visualisation(s) to allow a user to explore alternate constraint scenarios

#### Code introduction

Ipywidgets [14]: Library used to create the interactive visualization.

plotly.graph_objs[12]:  for creating interactive plots (go.Bar and go.Histogram).

I've decided to start the project's visualization component with the same values in the variables_domain, but I've modified the variable names to reduce the possibility of combining scripts. I've also used the same strategy when it comes to constraint.

`pre_selected` is used in the script without an argument since the dynamic visualization will choose which team members are pre-selected.

`meets_requirements`:  A function that checks if a particular combination of people meets the required skills. It tallies the skills of the combination and compares this against the skill_constraints to determine if it's a valid team setup.

#### Code Explanation

`__init__` : initializes a constructor for the pre-selected individuals calling the `init_ui_elements` initializing the interface elements.

he `init_ui_elements`: Using `skills_contraints` to create sliders. Also, create a slider for the total of people to be hired, and checkbox for the pre-selected individuals.

`Handle_preselected` uses `pre_selected` set to refresh the visualization in update_plot which is triggered every time any attribute on sliders and checkbox is changed.

`render_output` printing a new list of possible solution after clearing the previous output. After doing it calls render_visualization in order to update the plots.



### Create GUI(s) to allow a user to explore alternate constraint scenarios

#### Code Introduction

Customtkinter [3] used in Tkinter [13] for creating modern-looking GUI applications using tools such CTkSlider and CTkLabel.

FigureCanvasTkAgg powerful tool from matplotlib.backends.backend_tlagg [10 ] to embed the library into applications in Tkinter providing figures to be rendered within TKinter windows.

I've made the decision to start the project's visualization component with the same values in the variables_domain, but I am using for both problems so will run only once.

pre_selected is used in the script without an argument since the dynamic visualization will choose which team members are pre-selected.

meets_requirements function: A function that checks if a particular combination of people meets the required skills. It tallies the skills of the combination and compares this against the skill_constraints to determine if it's a valid team setup.


#### Code Explanation

`__init__`: Initializes the application window using customtkinter (ctk), sets the theme to dark, titles the window "Team Constraints Explorer", and sets its geometry.

Calls the `init_ui_elements` method to set up the user interface components.

Begins the Tkinter main loop to display the window.

`init_ui_elements` Uses customtkinter (ctk) widgets, the `init_ui_elements` function in the TeamExplorerApp class configures the user interface elements, resulting of a dynamic and interactive application for team constraints exploration.

•	`skill_constraint_sliders`: A slider is created for each `skill_constraints`, letting the user enter the number needed for each skill.
•	`total_people_slider`: A slider that allows the user to select how many workers in total they wish to hire.
•	`pre_selected_checks`: Individual checkboxes in `employee_skills`. Users have the option to pre-select particular members of the team.
•	`output_area`: A text box where, upon calculations, the potential teams will show up.

Because each interactive element—such as sliders and checkboxes—is connected to the `update_plot` function, any input from the user will instantly update and recalculate the teams and visualizations that are presented. With no more input from the user needed, this method produces a responsive user experience that updates in real-time.

`update_plot` Collects the most recent values from each checkbox and slider.

Use combination logic and the `meets_requirements` function to determine possible teams based on the existing requirements.

Adds the most recent possible team calculations to the output area.

Refresh any visualizations with the latest team data by using `update_visualization`.

`update_visualization` Creates or modifies a different top-level window just for visualizations.

Creates two subplots: one that displays how many employees work in teams and another that displays the range of team sizes.

Plots are created using matplotlib and shown in the Tkinter window.










## References

1. Barták, R., Morris, R.A. and K. Brent Venable (2014). CONSTRAINT PROPAGATION AND BACKTRACKING-BASED SEARCH A brief introduction to mainstream techniques of constraint satisfaction.

2. Brailsford, S.C., Potts, C.N. and Smith, B.M. (1999). Constraint satisfaction problems: Algorithms and applications. European Journal of Operational Research, 119(3), pp.557–581.

3. customtkinter.tomschimansky.com. (n.d.). Documentation Introduction | CustomTkinter. [online] Available at: https://customtkinter.tomschimansky.com/documentation/ .[Accessed 4 Jan. 2024].

4. docs.pulpproject.org. (n.d.). Pulp Documentation — Pulp Project 3.43.1 documentation. [online] Available at: https://docs.pulpproject.org/pulpcore/ [Accessed 4 Jan. 2024].

5. docs.python.org. (n.d.). itertools — Functions creating iterators for efficient looping — Python 3.9.1 documentation. [online] Available at: https://docs.python.org/3/library/itertools.html. [Accessed 4 Jan. 2024].

6. Hillier, F.S. and Lieberman, G.J. (2010). Introduction to operations research. New York, Ny: Mcgraw-Hill.

7. ipython.org. (n.d.). Module: display — IPython 3.2.1 documentation. [online] Available at: https://ipython.org/ipython-doc/3/api/generated/IPython.display.html [Accessed 4 Jan. 2024].

8. Knaflic, C.N. (2015). Storytelling with Data: A Data Visualization Guide for Business Professionals. Hoboken, New Jersey: Wiley.

9. matplotlib.org. (n.d.). Embedding in Tk — Matplotlib 3.6.0 documentation. [online] Available at: https://matplotlib.org/stable/gallery/user_interfaces/embedding_in_tk_sgskip.html. [Accessed 4 Jan. 2024].

10. matplotlib.org. (n.d.). matplotlib.backends.backend_tkagg — Matplotlib 3.3.4 documentation. [online] Available at: https://matplotlib.org/3.3.4/api/backend_tkagg_api.html [Accessed 4 Jan. 2024].

11. matplotlib.org. (n.d.). matplotlib.ticker — Matplotlib 3.7.2 documentation. [online] Available at: https://matplotlib.org/stable/api/ticker_api.html. [Accessed 4 Jan. 2024].

12. plotly.com. (n.d.). plotly.graph_objects.Figure — 5.14.1 documentation. [online] Available at: https://plotly.com/python-api-reference/generated/plotly.graph_objects.Figure.html. [Accessed 4 Jan. 2024].
13. Python Software Foundation (2019). tkinter — Python interface to Tcl/Tk — Python 3.7.2 documentation. [online] python.org. Available at: https://docs.python.org/3/library/tkinter.html. [Accessed 4 Jan. 2024].

14. Readthedocs.io. (2022). Widget List — Jupyter Widgets 8.0.0rc0 documentation. [online] Available at: https://ipywidgets.readthedocs.io/en/latest/examples/Widget%20List.html. [Accessed 4 Jan. 2024].

15. Rodriguez, T.S. (2022). Linear Programming: optimizing solutions with Python using PuLP. [online] Medium. Available at: https://medium.com/@telmosubirar/linear-programming-optimizing-solutions-with-python-using-pulp-e0c4379696c8 [Accessed 28 Dec. 2023].

16. Schaub, L. (2023). Modern Graphical User Interfaces using Python — Customtkinter. [online] Medium. Available at: https://medium.com/@lukasschaub/modern-graphical-user-interfaces-using-python-customtkinter-80f42b698eaf [Accessed 2 Jan. 2024].

17. Stuart Jonathan Russell; Peter Norvig (2010). Artificial Intelligence: A Modern Approach. Prentice Hall. p. Chapter 6.

18. Taha, H.A. (2017). Operations research an introduction. Boston: Pearson.

19. Wikipedia Contributors (2019). Constraint satisfaction problem. [online] Wikipedia. Available at: https://en.wikipedia.org/wiki/Constraint_satisfaction_problem . [Accessed 4 Jan. 2024].

20. www.cs.cmu.edu. (n.d.). Constraint Satisfaction Problems. [online] Available at: https://www.cs.cmu.edu/~15281/coursenotes/constraints/index.html [Accessed 28 Dec. 2023].














