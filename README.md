# Sprint-2
​1. Selected Topic
​System: Financial Transactions & Banking System.
Reasoning: This system was chosen to facilitate the exploration of complex relational mapping, high-stakes transaction processing (ACID properties), and performance benchmarking required in later milestones.  
​2. System Description (Real-World Data Mapping)
​The system is designed to model a commercial banking environment. It maps real-world financial entities into a digital schema to ensure data integrity and scalability:  
​Customer Management: Captures the legal identity of individuals or entities holding assets.  
​Account Tracking: Manages the lifecycle of financial products (Savings, Checking) and their liquid balances.  
​Transactional Ledger: A continuous, immutable record of fund movements to ensure financial accountability.  
​Organizational Hierarchy: Mapping accounts to specific banking branches for logistical and regional tracking.  
​3. Conceptual Model: Entities, Attributes, and Relationships
​To satisfy the requirements for identification of entities and constraints:  
​Entity: Customer
​Attributes: CustomerID (Primary Key), NationalID (Unique), FullName, Address, PhoneNumber.
​Entity: Account
​Attributes: AccountNumber (Primary Key), AccountType (Savings/Current), Balance, DateOpened.
​Relationship: One-to-Many with Customer (One customer can have multiple accounts).  
​Entity: Transaction
​Attributes: TransactionID (Primary Key), Amount, Timestamp, TransactionType (Credit/Debit).
​Relationship: Many-to-One with Account (Each transaction belongs to one account).  
​Entity: Branch
​Attributes: BranchCode (Primary Key), BranchName, Location.
​Relationship: One-to-Many with Account.  
​4. Initial Relational Schema Draft
​This draft serves as the bridge from the ER diagram to the SQL implementation required in Milestone 2.  
​Customers (\underline{\text{CustomerID}}, \text{NationalID}, \text{FullName}, \text{Address}, \text{Phone})  
​Branches (\underline{\text{BranchCode}}, \text{BranchName}, \text{Location})  
​Accounts (\underline{\text{AccountNumber}}, \text{AccountType}, \text{Balance}, \textit{CustomerID}, \textit{BranchCode})  
​Foreign Keys: CustomerID references Customers, BranchCode references Branches.
​Transactions (\underline{\text{TransactionID}}, \text{Amount}, \text{Timestamp}, \text{Type}, \textit{AccountNumber})  
​Foreign Key: AccountNumber references Accounts.
​5. Milestone 1 Self-Reflections
​As per the non-negotiable rules, every milestone must document the evolution process:  
​What Changed: We initially considered a "flat" structure for transactions but moved to a relational link to Accounts to support future normalization (BCNF) in Milestone 4.  
​What Failed: Attempting to include "Loan" details in the Account table led to data redundancy.  
​Why it Failed: A single account can have multiple loans, creating a multi-valued dependency.  
​Alternative Approach: We will separate "Loans" into its own entity in Milestone 2 to maintain design rigor.  
