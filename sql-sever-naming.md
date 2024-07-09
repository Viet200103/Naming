# SQL SEVER CONVENTIONS

---

reference: https://www.isbe.net/Documents/SQL_server_standards.pdf

---

### Table

* Using PascalCase
* Singular Name: **Customer** instead of **Customers**
* Don't use prefixes like "tb" or "TBL" unless they are deemed necessary to help organize tables.

  Example: **HcPayClients** not **PayHcClients**

* Junction tables be named by concatenating the names of the tables in relationship.

  Example: Doctors have many Patients and visa, JunctionName: **DoctorPatient**

### Columns

* Using PascalCase
* Avoid using abbreviations, or prefixes like **fld_** or **Col**
* **Primary key** should [TableName] + "Id"
* **Foreign Key** should have exact same name primary key of parent table
  or some case
    * Description before, example Address table, foreign key: WorkAddressId, ShippingAddressId
    * Readable SQL:

      **File inner join Directory on File.FileID = Directory.FileID**

    * Much confusion:

      **File inner join Directory on File.FileId_Pk = Directory.FileId_Fk**

### Indexes

> **{U/N}IX_{TableName}{SpecialPurpose}**
>
>**U/N**: unique or non-unique
>
>**IX_**: default prefix

### Constraints

> **{constraint type}{table name}_{field name}**
> **PK**: primary key
>
> **FK**: foreign key
>
> **CK**: check
>
> **UN**: unique
>
> **Example**:  PK_Products_Id

### Views

Named like the **Table** but with two differences

* Using prefix: **"vw"** before name
* For simple views that just join one or more tables with no selection criteria, combine the names of the tables joined.

  Example: joining the "Customer" and "StateAndProvince" table, name of view: "vwCustomerStateAndProvince".

### Stored procedures

* Do not use **"sp_"**, **"xp_"**, **"dt_"** prefix - default naming convention master database
* Procedures ordered by the table/business entity they perform a database operation on, and adding the database
  activity "Get, Save, or Delete" as a suffix, e.g.

  Example: ProductInfoGet, spProductInfoGet

* Produce return scalar value: combine verb and noun.

  Example: ValidateLogin
* **"sp"** prefix is acceptable and encouraged

### Function

* Apply naming stored procedures.
* **"fn"** prefix is acceptable and encouraged
* Named as a verb because of the function's return value

  Example: fnParseTableToString

* Scalar function do not need suffix but table-valued functions should indicate that they return a table by using a
  “Table” suffix.

### Trigger

* Apply naming stored procedures.
* **"tr"** prefix is acceptable and encouraged
* **Ins, Upd, or Del** as suffix

  Example: trProductsInsUpd, trProductsUpdDel
* Some systems allow multiple triggers per operation per table

  Example: trUsers_ValidateEmailAddress_Ins, trUsers_MakeActionEntries_Ins

### User-Defined Data Types

* **"ud"** prefix is acceptable and encouraged

### Variables

* Using camelCase

### SQL Statement
* SQL statement syntax use uppercase for all letters

```sql
DECLARE @var1 int
        
DECLARE MyCursor CURSOR LOCAL FAST_FORWARD FOR
        
SELECT Col2
FROM MyTable1
WHERE Col1 = 5
  
OPEN MyCursor
FETCH NEXT FROM MyCursor INTO @var1
WHILE (@@fetch_status <> -1)
BEGIN
    IF (@@fetch_status <> -2)
    BEGIN
        DELETE FROM MyTable2
        WHERE Col1 = @var1
    END
    FETCH NEXT FROM MyCursor INTO @var1
END
CLOSE MyCursor
DEALLOCATE MyCursor
```