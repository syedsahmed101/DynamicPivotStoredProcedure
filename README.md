# Description
SQL Stored Procedure to illustrate dynamically pivoting the data.

Dynamic slicing and dicing of data by transposing data into columns to help in data analysis.

# Sample Dataset
| Application Family | Environment | AppCount |
| ------------: | ------------: | -----------: |
| Record Keeping | Production | 50 |
| Record Keeping | Prod-DR | 50 |
| Record Keeping | UAT | 20 |
| Record Keeping | Development | 20 |
| Reporting and Metrics | Production | 10 |
| Reporting and Metrics | Prod-DR | 10 |
| Reporting and Metrics | UAT | 5 |
| Reporting and Metrics | Development | 5 |


```````````````````````````````````````
CREATE TABLE ApplicationCountByStatus(
  [ApplicationFamily] VARCHAR(50),
  [Environment] VARCHAR(50),
  [AppCount]   INT
)
GO


 
INSERT INTO ApplicationCountByStatus VALUES 
('Record Keeping','Production',50),
('Record Keeping','Prod-DR',50),
('Record Keeping','UAT',20),
('Record Keeping','Development',20),
('Reporting and Metrics','Production',10),
('Reporting and Metrics','Prod-DR',10),
('Reporting and Metrics','UAT',5),
('Reporting and Metrics','Development',5)
GO
`````````````````````````````````````````````

# Desired Output
| Application Family | Production | Prod-DR | UAT | Development |
| ------------- |:-------------:| -----:| -----:| ----:|
| Record Keeping | 50 | 50 | 20 | 20 |
| Reporting and Metrics | 10 | 10 | 5 | 5 |

# Execution
``````````````````````````````````````````
Exec dbo.DynamicPivotStoredProcedure N'Environment', N'Production, Prod-DR, UAT, Development'
