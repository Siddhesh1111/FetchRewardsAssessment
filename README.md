# FetchRewardsAssessment

# 1. Review Existing Unstructured Data and Diagram a New Structured Relational Data Model

![image](https://github.com/Siddhesh1111/FetchRewardsAssessment/assets/70564010/67b424c5-ceaa-4e99-8013-6e1043678dbb)


# 2. Write a query that directly answers a predetermined question from a business stakeholder

Write a SQL query against your new structured relational data model that answers one of the following bullet points below of your choosing. Commit it to the git repository along with the rest of the exercise. Note: When creating your data model be mindful of the other requests being made by the business stakeholder. If you can capture more than one bullet point in your model while keeping it clean, efficient, and performant, that benefits you as well as your team.
<ul>
  <li>What are the top 5 brands by receipts scanned for most recent month?</li>
  <li>How does the ranking of the top 5 brands by receipts scanned for the recent month compare to the ranking for the previous month?</li>
  <li>When considering average spend from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?</li>
  <li>When considering total number of items purchased from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?</li>
  <li>Which brand has the most spend among users who were created within the past 6 months?</li>
  <li>Which brand has the most transactions among users who were created within the past 6 months?</li>
</ul>

SOLUTION: [Access the solution queries here](https://github.com/Siddhesh1111/FetchRewardsAssessment/blob/main/SQL%20queries.docx)

# 3. Evaluate Data Quality Issues in the Data Provided

Using the programming language of your choice (SQL, Python, R, Bash, etc...) identify at least one data quality issue. We are not expecting a full blown review of all the data provided, but instead want to know how you explore and evaluate data of questionable provenance.

Commit your code and findings to the git repository along with the rest of the exercise.

SOLUTION: [Access your solution file here](https://github.com/Siddhesh1111/FetchRewardsAssessment/blob/main/Fetch%20Rewards%20Data%20Analyst.ipynb)

# 4. Communicate with Stakeholders

Construct an email or slack message that is understandable to a product or business leader who isn’t familiar with your day to day work. This part of the exercise should show off how you communicate and reason about data with others. Commit your answers to the git repository along with the rest of your exercise.

<ul>
  <li>What questions do you have about the data?</li>
  <li>How did you discover the data quality issues?</li>
  <li>What do you need to know to resolve the data quality issues?</li>
  <li>What other information would you need to help you optimize the data assets you're trying to create?</li>
  <li>What performance and scaling concerns do you anticipate in production and how do you plan to address them?</li>
</ul>


SOLUTION:
Email
<div>
  <h4>Subject: Data Quality Issues anf Optimization Opportunities</h4>
  Respected [Product Manager]<br>
  <p>I hope this message finds you well. I wanted to bring to your attention some important findings regarding our data quality and optimization opportunities. As our team has been working extensively with data, we have identified a few issues that require attention and have also discovered potential avenues for improving our data assets.</p>
  <ol>
    <li>
I would like to seek clarification regarding the correlation between the brand barcode and the product barcode as depicted in the receipts. I have been operating under the assumption that these barcodes should align with each other. However, upon conducting my analysis, I have observed numerous instances where the barcodes do not match up. In the event that they are indeed dissimilar, I kindly request an explanation regarding how brands are associated with items within a receipt. This matter raises significant concern and requires immediate attention for us to ensure accuracy and coherence in our data analysis.</li>
    <li>There are significant issues with brand codes in our data. Specifically, we have identified 54 instances where the brand code field displays the barcode instead of the actual brand code value. Additionally, we have approximately 234 missing brand codes. This situation requires immediate attention from the product catalog team to rectify the problem and provide the accurate brand code values.</li>
    <li> I have identified approximately 117 users who have receipts but are missing from the Users table. Additionally, we have detected duplicate entries in the Users table. This situation necessitates immediate action to address the issue. It is possible that this discrepancy is related to a bug in the app affecting user registration.</li>
  </ol>
</div>


# Our Data

<h3>Receipts Data Schema</h3>
<ul>
  <li>_id: uuid for this receipt</li>
  <li>bonusPointsEarned: Number of bonus points that were awarded upon receipt completion
</li>
  <li>bonusPointsEarnedReason: event that triggered bonus points
</li>
  <li>createDate: The date that the event was created
</li>
  <li>createDate: The date that the event was created
</li>

  <li>dateScanned: Date that the user scanned their receipt
</li>
  <li>finishedDate: Date that the receipt finished processing
</li>
  <li>modifyDate: The date the event was modified
</li>
  <li>pointsAwardedDate: The date we awarded points for the transaction
</li>
  <li>pointsEarned: The number of points earned for the receipt
</li>
  <li>purchaseDate: the date of the purchase
</li>
<li>purchasedItemCount: Count of number of items on the receipt
</li>
<li>rewardsReceiptItemList: The items that were purchased on the receipt
</li>
<li>rewardsReceiptStatus: status of the receipt through receipt validation and processing
</li>
<li>totalSpent: The total amount on the receipt
</li>
<li>userId: string id back to the User collection for the user who scanned the receipt
</li>
</ul>

<h3>Users Data Schema</h3>
<ul>
  <li>_id: user Id</li>
  <li>state: state abbreviation</li>
  <li>createdDate: when the user created their account</li>
  <li>lastLogin: last time the user was recorded logging in to the app
</li>
  <li>role: constant value set to 'CONSUMER'
</li>
  <li>active: indicates if the user is active; only Fetch will de-activate an account with this flag
</li>
</ul>




<h3>Brand Data Schema</h3>
<ul>
  <li>_id: brand uuid
</li>
  <li>barcode: the barcode on the item
</li>
  <li>brandCode: String that corresponds with the brand column in a partner product file
</li>
  <li>category: The category name for which the brand sells products in
</li>
  <li>categoryCode: The category code that references a BrandCategory
</li>
  <li>cpg: reference to CPG collection
</li>
  <li>topBrand: Boolean indicator for whether the brand should be featured as a 'top brand'
</li>
  <li>name: Brand name
</li>
</ul>
