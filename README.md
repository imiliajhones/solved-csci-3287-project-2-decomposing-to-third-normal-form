Download Link: https://assignmentchef.com/product/solved-csci-3287-project-2-decomposing-to-third-normal-form
<br>
<strong>Description</strong>

This project makes use of the database you installed for the first project.  If you have not modified the data or schemas associated with the original tables that were installed when you imported the database, you should be able to begin with the existing database.  Otherwise, reinstall the employee database as described in Project 1.




This project will use interview grading.  40% of your grade will be based on the submitted materials.  The remaining 60% will come from the interview portion.  You must schedule an interview slot with a grader.  If you do not schedule or attend a slot the interview portion will be scored zero.




<strong>Procedure</strong>

You will be given a table derived from the employee database and a set of functional dependencies.  You should complete the following steps




<ol>

 <li>Create the database table to be decomposed.  Execute the following query:</li>

</ol>




<strong>create view base as select dept_manager.emp_no,</strong>

<strong>    departments.dept_no,</strong>

<strong>    dept_name,</strong>

<strong>    dept_manager.from_date as dept_mgr_from_date,</strong>

<strong>    dept_manager.to_date as dept_mgr_to_date,</strong>

<strong>    title,</strong>

<strong>    titles.from_date as title_from_date,</strong>

<strong>    titles.to_date as title_to_date</strong>

<strong>from departments, dept_manager, titles</strong>

<strong>where departments.dept_no = dept_manager.dept_no and</strong>

<strong>    dept_manager.emp_no = titles.emp_no;</strong>




This query yields a view called <strong>base </strong>that you will need to decompose.







<ol>

 <li>What should be the key for this table?</li>

</ol>

(dept_no, dept_mgr_from_date, dept_mgr_to_date, title_from_date, title_to_date)

<ol>

 <li>You have as inputs the attributes of the <strong>base </strong>table, the key you just determined, and the following functional dependencies:</li>

</ol>




<ol>

 <li>If you know the department number, you know the department name.</li>

</ol>

dept_no -&gt; dept_name




<ol>

 <li>There can only be one department manager at the same time.</li>

</ol>

dept_mgr_from_date, dept_mgr_to_date, dept_no -&gt; emp_no




<ol>

 <li>Each employee can only hold one title at the same time.</li>

</ol>

emp_no, title_from_date, title_to_date -&gt; title







<ol>

 <li>Derive the 3NF form for this table.  Write the proper queries to generate the decomposed tables as views.  You should be able to explain during the grading interview how you applied the 3NF Synthesis algorithm.</li>

</ol>

R1: create view R1 as select emp_no, title, title_from_date, title_to_date from base;




R2: create view R2 as select distinct dept_mgr_from_date, dept_mgr_to_date, dept_no, emp_no from base;




R3: create view R3 as select distinct dept_no, dept_name from base;




R4: create view R4 as select dept_no, dept_mgr_from_date, dept_mgr_to_date, title_from_date , title_to_date from base;




<ol>

 <li>Provide the output of each table in a separate file, tar these files together and submit them to moodle.</li>

</ol>







There is ambiguity in this specification intentionally.  The intent of the assignment is to gauge your ability to execute this process with fuzzy specs, which is what will happen in the real world.  As a result, there will be variations in the final answers.  Grading will be done based on how you derive the 3NF and how well you execute each of the individual steps.  A sample solution will be published afterwards but this sample serves as a guide for the grading rather than being the definitive solution.