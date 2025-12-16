# AWS Challenge Lab: Amazon DynamoDB Music Library
![AWS Lab Banner](./images/aws-banner.png)
<!-- Upload your banner image to: repository_root/images/aws-banner.png -->

## Hey! Welcome to My AWS Lab Journey 👋

You're looking at the documentation for an AWS Challenge Lab I completed, where I worked with Amazon DynamoDB to build and manage a NoSQL database. It was a hands-on exercise that pushed me to understand the fundamentals of serverless database management and flexible data modeling.

## What I Set Out to Do

The challenge was straightforward but required real execution:

1. **Create a DynamoDB table** with a partition key and sort key for a music library
2. **Populate the database** with music data using flexible schemas
3. **Query and scan the data** to retrieve specific items efficiently
4. **Clean up resources** by deleting the table when finished

No shortcuts, no copy-paste solutions—just me, the AWS Console, and a NoSQL database to build from scratch.

---

## How I Tackled It

### Getting Started: Launching the Environment

First thing I did was fire up the AWS lab environment. Once everything showed "Ready," I had access to the AWS Management Console with full DynamoDB permissions. The green circle indicated I was good to go.

**Figure 1: Lab environment ready and AWS Console access confirmed**

![Lab Details Screenshot](./images/lab-details.png)
<!-- Upload to: repository_root/images/lab-details.png -->

### Building the Foundation: Creating the DynamoDB Table

I navigated to the DynamoDB service and created a new table called "Music." The key design decision here was choosing the right primary key structure—I went with a composite key using `Artist` as the partition key and `Song` as the sort key. This combination would uniquely identify each track in the library.

**Figure 2: Configuring the Music table with partition and sort keys**

![Table Creation Screenshot](./images/table-creation.png)
<!-- Upload to: repository_root/images/table-creation.png -->

### The Fun Part: Adding Data with Flexible Schemas

Now came the actual data entry. I used the DynamoDB console to create items, and this is where NoSQL really shines.

Here's what my data structure did:
- Started with required fields only (Artist and Song)
- Added different attributes to different items (Album, Year, Genre, LengthSeconds)
- Demonstrated schema flexibility—each item could have unique attributes without pre-defining them
- Created three distinct music entries: Pink Floyd's "Money," John Lennon's "Imagine," and Psy's "Gangnam Style"

Nothing fancy, just solid NoSQL principles in action.

**Figure 3: First item created with core attributes**

![First Item Screenshot](./images/first-item.png)
<!-- Upload to: repository_root/images/first-item.png -->

**Figure 4: Additional items showing schema flexibility**

![Multiple Items Screenshot](./images/multiple-items.png)
<!-- Upload to: repository_root/images/multiple-items.png -->

### Course Correction: Modifying an Existing Item

I caught an error in my data—Psy's "Gangnam Style" was listed as 2011, but it was actually released in 2012. I navigated to the item through the Explore Items interface and updated the Year attribute. Simple fix, but it showed how straightforward data updates are in DynamoDB.

**Figure 5: Editing the item to correct the year**

![Item Modification Screenshot](./images/item-modification.png)
<!-- Upload to: repository_root/images/item-modification.png -->

### The Moment of Truth: Querying and Scanning

I tested both query methods DynamoDB offers. First, I ran a query operation using the partition key (Psy) and sort key (Gangnam Style)—lightning fast, fully indexed retrieval. Then I ran a scan operation with a filter on the Year attribute to find songs from 1971. The query was instant; the scan had to examine every item.

**Figure 6: Query operation showing efficient retrieval**

![Query Results Screenshot](./images/query-results.png)
<!-- Upload to: repository_root/images/query-results.png -->

**Figure 7: Scan operation with filter applied**

![Scan Results Screenshot](./images/scan-results.png)
<!-- Upload to: repository_root/images/scan-results.png -->

### Cleanup: Deleting the Table

Finally, I deleted the Music table to avoid any unnecessary charges. DynamoDB made this straightforward—selected the table, chose Delete, typed the confirmation, and it was gone along with all its data.

**Figure 8: Table deletion confirmation**

![Table Deletion Screenshot](./images/table-deletion.png)
<!-- Upload to: repository_root/images/table-deletion.png -->

---

## What I Learned

This wasn't just about creating a database table. The real value was in:

- **NoSQL Data Modeling** - I experienced firsthand how schema flexibility allows different items to have different attributes without migration headaches
- **DynamoDB Query Patterns** - I learned the crucial difference between queries (fast, indexed) and scans (slow, full table examination)
- **Serverless Database Management** - I gained hands-on experience with a fully managed database service that requires zero server administration

It's one thing to read about NoSQL databases. It's another to build one and see how the partition key and sort key architecture enables massive scalability.

---

## Repository Contents

```
.
├── images/                      # Screenshots documenting the process
│   ├── aws-banner.png
│   ├── lab-details.png
│   ├── table-creation.png
│   ├── first-item.png
│   ├── multiple-items.png
│   ├── item-modification.png
│   ├── query-results.png
│   ├── scan-results.png
│   └── table-deletion.png
├── music-data-samples.json      # Sample data structure (if included)
└── README.md                    # You're reading it
```

---

## Want to Try This Yourself?

If you have access to AWS and want to replicate this:

1. Open the DynamoDB console and create a table with a partition key and sort key
2. Add items with varying attributes to see schema flexibility in action
3. Practice both query and scan operations to understand the performance difference
4. Delete the table when finished to avoid charges

It's a simple exercise, but it builds real cloud database muscle.

---

## Tech Stack

- **Cloud Platform:** AWS DynamoDB
- **Database Type:** NoSQL (Key-Value/Document Store)
- **Access Method:** AWS Management Console
- **Tools:** DynamoDB Console, Query/Scan operations

---

*Completed as part of AWS Training & Certification Challenge Lab*

![Footer](./images/footer.png)
<!-- Upload to: repository_root/images/footer.png -->
