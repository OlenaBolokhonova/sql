# Assignment 1 by Olena Bolokhonova: Design a Logical Model

## Question 1

Create a logical model for a small bookstore. 📚
# Created and added a logical model olena_bolokhonova_design_a_logical_model.png

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.
# Added to the ERD employee shifts, updated a logical model olena_bolokhonova_design_a_logical_model_shifts.png

## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
The store may use one of these two distinct architectures for the Customer_Address table:
One design that overwrites changes (Type 1 SCD).
One design that retains changes (Type 2 SCD).

Type 1 Slowly Changing Dimension (SCD): Overwriting Changes
In this design, each time we update the customer address, it replaces the previous one. This means only the current address is kept, and we don't save any historical data.
Customer_Address (Type 1):
customer_id (Primary Key, Foreign Key)
address_line_1
address_line_2
city
province
postal_code
country

Type 2 Slowly Changing Dimension (SCD): Retaining Changes
In this design, every time we update the customer address, a new record is created. This way, we keep historical data and can track the changes in addresses over time.
Customer_Address (Type 2):
address_id (Primary Key)
customer_id (Foreign Key)
address_line_1
address_line_2
city
province
postal_code
country
address_start_date
address_end_date
is_curent (Boolean): if this is the current address (true or false).

Privacy Implications
Type 1 (Overwriting Changes):
Pros: Simpler data management with fewer records.
Cons: Lack of historical data might be a disadvantage for auditing and tracking purposes.

Type 2 (Retaining Changes):
Pros: Provides a detailed history of changes, useful for auditing and tracking.
Cons: Storing historical addresses may pose privacy risks, especially if old addresses are sensitive. Proper data protection measures, such as encryption and access controls, are necessary to mitigate these risks.

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
The AdventureWorks schema is highly detailed and organized into specific spheres. 
Here are the key differences between my version of ERD and the AdventureWorks schema:

1. Scope and Coverage:
AdventureWorks: Covers a wide range of business areas such as sales, purchasing, person, production, and human resources. It provides a comprehensive model for an enterprise-level application.
My ERD: the first version of my ERD was focused on core entities related to a bookstore, including Employee, Order, Sales, Customer, and Book, before adding additional entities inspired by AdventureWorks.
2. Entity Relationships:
AdventureWorks: Contains complex relationships with many-to-many relationships, associative entities, and multiple hierarchical structures.
My ERD: Started with simpler one-to-many and many-to-one relationships but has been enhanced to include more entities and relationships.
3. Attribute Details:
AdventureWorks: Attributes are well-detailed, including various constraints, data types, and relationships between multiple tables.
My ERD: Attributes are likely less detailed initially, but I have improved the granularity of attributes.
4. Complexity:
AdventureWorks: Is more complex with more tables and intricate relationships.
My ERD: Has grown more complex with the addition of new tables 
5. Normalization:
AdventureWorks: Likely has higher levels of normalization to reduce redundancy and ensure data integrity.
My ERD: Has been moving towards higher normalization levels inspired by AdventureWorks.

Inspired by the AdventureWorks schema, I decided to add the following tables to mine ERD:
Publisher
Shopping_basket_book
Warehouse
Warehouse_book
Shipment
Additionally, I established relationships between these new tables and identified PK, FK, and U constraints in my tables.

# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `June 1, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
