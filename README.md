# TRMS

An angular application that allows the employee user to log in and approve submissions for Tuition Reimbursement.  Employees are categorized into various departments and roles.  The application limits who can approve at what stage.  It gives different privileges depending on role designation such as Benefits Coordinator or Department Head.  Department Head must reside in the same department as the requester in order to proceed.  

Technologies Used

    Angular 
    Java 8
    JUnit

Features

List of features ready and TODOs for future development

    Allows users to approve or deny requests for tuition reimbursement in a table format.
    Allows users to request tuition reimbursement for courses that they've taken.
    

To-do list:

    More front-end testing using Jasmine. 
    End-to-end testing using Selenium.

Getting Started


    In the GitBash window, please type git clone https://github.com/LydiaB71/TRMS.git
    It uses a local database so DML statements that set up the schema would need to be implemented as follows:
    
    create table role_type(
    id integer primary key,
    role_name varchar(20)
);

create table department(
    id integer primary key,
    dept_name varchar (20)
);

create table employee (
	id serial primary key,
	emp_password varchar(15) not null,
	first_name varchar(10) not null,
	last_name varchar(10) not null,
	emp_location varchar(10),
	department integer references department,
	emp_role integer references role_type,
	emp_role2 integer,
	funds float
	
	);

create table event_type(
    id integer primary key,
    event_name varchar(15),
    reimb_percnt float
);

create table course (
    id serial primary key,
    employee_id integer references employee,
    start_date varchar(10),
	start_time varchar(10),
	description varchar(25),
	course_cost float,
	grading_format varchar(15),
	event_type_id integer references event_type,
	dir_sup varchar (15),
	dept_head varchar(15),
	ben_cor varchar(15),
	award_granted varchar (15),
	approver_id integer
);
   
 Next you need to insert some values into the tables as follows:
 insert into role_type values (1, 'student');
insert into role_type values (2, 'direct supervisor');
insert into role_type values (3, 'department head');
insert into role_type values (4, 'benefits coordinator');

insert into event_type values (1, 'certification',1);
insert into event_type values (2, 'tech training',.9);
insert into event_type values (3, 'univ courses',.8);
insert into event_type values (4, 'cert prep class',.75);
insert into event_type values (5, 'seminar',.6);
insert into event_type values (6, 'other',.3);

insert into employee values (1, 'pass', 'Crystal', 'Smith', 'Houston', 1, 1,0,1000);
insert into employee values (2, 'pass', 'Linda', 'Brown', 'Houston', 2, 2 ,0, 1000);
insert into employee values (3, 'pass', 'Barbara', 'Smith', 'Houston', 3, 3,0,1000);
insert into employee values (4, 'pass', 'Paul', 'Smith', 'Houston', 4, 4,0, 1000);
insert into employee values (5, 'pass', 'Lois', 'Glynn', 'Lake Tahoe', 2, 3, 4,1000);

Usage

    Once the database is set up, you will need to load the Java back-end into your IDE such as Eclipse.  Then you'll need to run a server like Tomcat.  Next, you'll want to go to your front-end code in an IDE such as Visual Studio Code and run ng serve -o at the terminal window.  This will invoke the Angular application to run.  Once the application is running you should be able to log in using the employee number and password that you inserted into the employee table above.  This will be the main way you will interact with the application.  
