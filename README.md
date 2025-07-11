      # project
    Capstone project submission
[employee-.pbix.zip](https://github.com/user-attachments/files/21112113/employee-.pbix.zip)
[ amazon case study answer.xlsx](https://github.com/user-attachments/files/21112126/amazon.case.study.answer.xlsx)
                  Case Study (1)
1. Average discount percentage by product category
Add a calculated column:
= (Actual Price - Discounted Price) / Actual Price * 100

Then use a Pivot Table:

Rows: Category

Values: Discount % → summarize by Average

2. How many products are listed under each category
Pivot Table:

Rows: Category

Values: Product Name → set to Count (Distinct)

3. Total number of reviews per category
Use Rating Count column

Pivot Table:

Rows: Category

Values: Rating Count → Sum

4. Which products have the highest average ratings
Sort your dataset by the Average Rating column (descending)

Pick top entries

5. Average actual price vs discounted price by category
Pivot Table:

Rows: Category

Values: Actual Price → Average
Discounted Price → Average

6. Which products have the highest number of reviews
Sort Rating Count column in descending order

7. How many products have a discount of 50% or more
Add calculated column:
=IF(Discount % >= 50, "Yes", "No")

Then use a COUNTIF

8. Distribution of product ratings
Pivot Table:

Rows: Rating (rounded if needed)

Values: Product Name → Count.  

9. Total potential revenue by category (Actual Price × Rating Count)
Add calculated column:
=Actual Price * Rating Count

Pivot Table:

Rows: Category

Values: Potential Revenue → Sum

10. Number of unique products per price range bucket
Create new column Price Bucket:

Excel formular=IF(Discounted Price < 200, "<₹200",
   IF(Discounted Price <= 500, "₹200–₹500", ">₹500")) (they should take note of the symbol for some systems)
11. Pivot Table:

Rows: Price Bucket

Values: Product Name → Count

12. How many products have fewer than 1,000 reviews
Filter Rating Count < 1000

Use COUNT or check the status bar, count is there.

13. Which categories have products with the highest discounts
Use the earlier Discount % column

Pivot Table:

Rows: Category

Values: Discount % → Max

14. Top 5 products by rating + number of reviews combined
Create calculated column:
=Average Rating + (Rating Count / Scaling Factor)
(Choose a factor like 1000 to balance weight)

Sort descending and pick top 5.
Use COUNT or check the status bar, count is there.

      Case Study (2)
Using Power BI
2: Ratings Insights Based on Gender
1. Create a histogram/box plot:
    - Axis: Rating
    - Value: Count of Employees by Gender
2. Use a slicer to filter by gender.
3. Calculate the average rating by gender using a measure.

Visualization:
- Histogram: "Ratings Distribution by Gender"
- Box plot: "Ratings Comparison by Gender"

Measures
- `Average Rating by Gender = AVERAGE('Employee'[Rating])`
- `Rating Count by Gender = COUNT('Employee'[Rating])`


3: Salary Structure and Gender Pay Gap Analysis
1. Create a scatter plot:
    - X-axis: Salary
    - Y-axis: Gender
2. Calculate the average salary by gender using a measure.
3. Identify departments and regions with significant pay gaps.

Visualization:
- Scatter plot: "Salary vs. Gender"
- Bar chart: "Average Salary by Department and Region"

Measures 
- `Average Salary by Gender = AVERAGE('Employee'[Salary])`
- `Salary Count by Department and Region = COUNT('Employee'[Salary])`
4: Minimum Salary Requirement Analysis
1. Create a histogram:
    - Axis: Salary Band ($10,000 increments)
    - Value: Count of Employees
2. Use a slicer to filter by region.
3. Calculate the number of employees below the minimum salary threshold.

Visualization:
- Histogram: "Salary Distribution by $10,000 Band"
- Bar chart: "Employees Below Minimum Salary Threshold by Region"

Measures
- `Employees Below Minimum Salary = COUNTX(FILTER('Employee', 'Employee'[Salary] < 90000), 'Employee'[Salary])`
- 4: Minimum Salary Requirement Analysis
1. Create a histogram:
    - Axis: Salary Band ($10,000 increments)
    - Value: Count of Employees
2. Use a slicer to filter by region.
3. Calculate the number of employees below the minimum salary threshold.

Visualization:
- Histogram: "Salary Distribution by $10,000 Band"
- Bar chart: "Employees Below Minimum Salary Threshold by Region"

Measures
- `Employees Below Minimum Salary = COUNTX(FILTER('Employee', 'Employee'[Salary] < 90000), 'Employee'[Salary])`
5: Bonus Payment Calculation
1. Create a measure to calculate the bonus amount based on performance ratings.
2. Calculate the total amount to be paid to individual employees (salary + bonus).
3. Create a bar chart to visualize the total amount to be paid out per region.

Visualization:
Bonus Payments
- Bar chart: "Total Bonus Payout by Region"
- Table: "Individual Employee Bonus Payments"

Measures
- `Bonus Amount = IF('Employee'[Rating] > 3, 'Employee'[Salary] * 0.1, 0)`
- `Total Amount to be Paid = 'Employee'[Salary] + 'Bonus Amount'`
