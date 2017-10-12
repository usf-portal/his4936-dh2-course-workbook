# Assignments

## Week 1 - Digital Modeling
* First week, no assignments due

## Week 2 - Programming Objects & SQL
* Head to Codecademy and Start the SQL Course
    * Complete Unit 1: Manipulation
    * If possible, complete Unit 2: Queries, though it is okay if you do not
    * Submit a screenshot of your progress
* Provide a 'sketch' of objects from an imaginary project [(see examples)](examples.md)
    * You must include 3-4 coherent models, or more if you wish
    * If possible, base your models on real historical sources
    * You must declare all of the fields and their data types
    * Some of your models must contain relationships to other models via Foreign Keys

## Week 3 - Cancelled Due to Inclement Weather

## Week 4 - What are Data?
* Head Back to Codecademy
    * Complete Unit 2, if you did not last week, and submit the screenshot
* Read the following...
    - Miriam Posner, ["Humanities Data: A Necessary Contradiction"](http://miriamposner.com/blog/humanities-data-a-necessary-contradiction)
    - Miriam Posner, ["What's Next, The Radical Unrealized Potential of Digital Humanities"](http://miriamposner.com/blog/whats-next-the-radical-unrealized-potential-of-digital-humanities)
* On Canvas, submit a one paragraph description of a project you might be interested in pursuing. If you already have a source of data in mind, make sure to include that. If you don't know what you want to research yet, tell me in what subjects you might want to start looking.

## Week 5 - Designing Schema and the Anatomy of a Query
* Head Back to Codecademy
    * EITHER go to the SQL course and complete unit 3, and submit a screenshot
    * OR go to the Python course and complete unit's 6-8, and submit a screenshot
* Locate a real historical source(s) that might serve as fodder for a project
    * Where to Look
        * Special Collections
        * Sources published non-digitally
        * If it is digital already, what can you add?
    * Learn as much as you can about said source(s)
        * When was it produced?
        * How can it be accessed?
        * What are difficulties in turning it digital?
    * **Come to class prepared to talk about how we might explore it.**

## Week 6 - No Homework

## Week 7 - Modeling

* Read BOTH of the following carefully, and refer back to it when making your dB models
    * [Celtic Inscribed Stones Project, Introduction to Databases](http://www.ucl.ac.uk/archaeology/cisp/database/manual/node1.html), a short easier read about databases written by digital humanists who worked the Celtic Inscribed Stones Project
    * [Introduction to db modeling](http://datanamic.com/support/lt-dez005-introduction-db-modeling.html), a slightly more advanced explanation. Some material will repeat what you read above, but will go into more detail. This was written by people who specialize in databases.
* Create a model of an historical source that you want to use for your project
    * Your model must have at least 4 tables
    * Your model should contain relationships *between* the tables (including many-to-many joins)
    * Submit your model (the .mwb file created by Workbench) on Canvas
    * Be prepared to talk about your model in class

## Week 8 - When the Plan Meets the Enemy

* Model and Data Entry for the [Julia Domna Inscriptions of the Severan Coin Database](http://web3.forest.usf.edu/main/other/severan/jdi/)
    * In Workbench
        * Create a Model file (.mwb) for the Julia Domna Inscriptions
        * Create tables for the inscriptions and people places etc... that appear on them
        * Make any other necessary tables to record relationships
        * You may use multiple EER (entity relationships) diagrams
    * In Excel
        * Create a Workbook file (.xlsx) for the data for your models
        * Create a worksheet for every table (rename the worksheet to the same name as the table)
        * Attempt to do the full data entry for **10** inscriptions. That means recording all of the entities for your tables, and the relationships between them, that can be found on those 10 inscriptions
    * On Canvas, submit your .mwb and your .xlsx file

## Week 9

* Read the following...
    * [The Programming Historian - Creating Network Diagrams from Historical Sources](https://programminghistorian.org/lessons/creating-network-diagrams-from-historical-sources)
    * [Microsoft - Database Design Basics] - https://support.office.com/en-us/article/Database-design-basics-eb2159cf-1e30-401a-8084-bd4f9c9ca1f5
    * [LucidChart - Database Structure and Design Tutorial](https://www.lucidchart.com/pages/database-diagram/database-design)
    * **OPTIONAL READ** [The Programming Historian - Exploring and Analyzing Network Data with Python](https://programminghistorian.org/lessons/exploring-and-analyzing-network-data-with-python)
* Create the select statements for 4 views of the sample database at thePortus
    * Your views should make sense for some likely use of the datebase. For example, it might contain ordering information for customers on a website... or for a business report used by a company for internal analysis
    * All views must all JOIN at least two tables together
    * At least one of the views should perform some kind of aggregation (using GROUP BY and some kind of function like SUM)
