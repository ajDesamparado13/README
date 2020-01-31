# Project Software Quality

## Base Requirements<a name="base-requirements"></a>

To ensure the quality of the software project, the following are the ideal base requirements for every project.

- The website of a particular project should be able to load completely at the maximum of 4 seconds page-load.
- Each functionality of the project should be able to complete it's process within 3 seconds mark with the exception of following: download, upload, and other long-term processes.
- The software should be able to log errors on application logs, e-mail and slack channel logging.
- Mobile design ready and performance is optimized for mobile devices

## Source Code Quality<a name="source-code-quality"></a>

To ensure the quality of the software source code, the following coding design principles must be observed on implementation from the order of highest precedence to lowest precedence.

- SOLID
  - Single Responsibility Principle
    - A class should have only a single responsibility (i.e only one potential change in the software's specification should be able to affect the specification of the class)
  - Open/Closed Principle
    - A software module ( it can be class or method) should be open for extensions but closed for modification
  - Liskov Substitution Principle
    - Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program
  - Interface Segregation Principle
    - Clients should not be forced to depend upon the interfaces that they do not use
  - Depedency Inversion Principle
    - Program to an interface, not an implementation
- KISS
  - Keep it simple and succinct
- DRY
  - Don't repeat yourself

should any of the principles conflict with one another the order of precedence is to be followed unless permitted by lead-developer.

## Delivery

### Delivering the project

To ensure the satisfaction of client before a project is delivered, The ISO/IEC 25010:2011 Software Quality must be observed.

### Delivering a fix, enhancement and deliverables.

To ensure the satisfication of client before a deliverable is handed to the client, the process of software delivery must be observed.

1. Member developer implements the code for a deliverable to be commited
2. Member developer should test the deliverable first on his/her local-machine before handing it over.
3. Lead Developer will then review the member developer code
   - in the case a request for change is raised, the process is back to step 1.
4. Lead Developer will then test the deliverable on staging server before handing it over to the Quality Assurance team.
   - in the case a bug / issue is found, an issue is raised, tagging the member.
5. The deliverable is then handed over to the Quality Assurance Team for in-depth testing.
   - in the case a bug / issue is found, an issue is raised, tagging both member and lead developer
6. Quality Assurance Team will then inform the project-manager of the deliverable state.
7. Project manager informs the client of the deliverable update.
8. Client tests the deliverable in staging server. hopefully satisfied;
   - in the case a bug / issue is found, an issue is then raised by project manager, tagging both QA,member and lead developer
9. Client approves of the deliverable to be released to production server.
10. An assigned DevOps will then merged the release to production server.

> Note:
>
> The precendence of person assigned for company to client communication is as follows:
>
> - Project Manager
> - Quality Assurance Manager
> - Lead Developer
> - Quality Assurance checker
> - Member Developer
