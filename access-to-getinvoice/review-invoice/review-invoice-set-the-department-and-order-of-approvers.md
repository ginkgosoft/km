# Review Invoice, Set the department and Order of approvers

Administrators can define departments and the order of approvers. All departments must set the same highest level of approvers. Explained as below,

|                         ผู้อนุมัติ                         |               ลำดับผู้อนุมัติ              |                                     แผนก                                     | คำอธิบาย                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| :--------------------------------------------------------: | :----------------------------------------: | :--------------------------------------------------------------------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|         <p>Account 1<br>Account 2<br>Account 3</p>         |    <p>No. 1</p><p>No. 2</p><p>No. 2</p>    |           <p>Not set department<br>department A<br>department B</p>          | <p>Account 1: Able to see all the items of every department and approve the items. The items will be shown the 2nd.<br>Account 2: Able to only see the list in Department A and approve REVIEWED ITEMS successfully.</p><p>Account 3: Able to see only the list in Department B and approve REVIEWED ITEMS successfully.</p>                                                                                                                |
|         <p>Account 1<br>Account 2<br>Account 3</p>         |    <p>No. 1</p><p>No. 2</p><p>No. 3</p>    |        <p>department A<br>Not set department<br>Not set department</p>       | <p>Account 1: Able to see only the list in Department A and approve items. The items will show be shown the 2nd.<br>Account 2: Able to see all the items of every department and approve the items. The items will be shown the 3rd.<br>Account 3: Able to see all the items of every department and approve the items. The items will be reviewed successfully.</p>                                                                        |
| <p>Account 1<br>Account 2<br>Account 3</p><p>Account 4</p> | <p>No. 1<br>No. 1<br>No. 2</p><p>No. 2</p> | <p>department A</p><p>department B</p><p>department A</p><p>department B</p> | <p>Account 1: Able to see only the list in Department A and approve items. The items will be shown the 2nd.<br>Account 2: Able to see only the list in Department B and approve items. The items will show be shown on the 2nd.</p><p>Account 3: Able to see only the list in Department A and approve REVIEWED ITEMS successfully.</p><p>Account 4: Able to see only the list in Department B and approve REVIEWED ITEMS successfully.</p> |

[<mark style="color:green;">Column description of Screen Review Invoice</mark>](#user-content-fn-1)[^1]

| ลำดับ |                    คอลัมน์                   |               รายละเอียด              |
| :---: | :------------------------------------------: | :-----------------------------------: |
|   1.  |  ![](<../../.gitbook/assets/image (77).png>) |                View PDF               |
|   2.  |  ![](<../../.gitbook/assets/image (25).png>) |                View XML               |
|   3.  |                    Item ID                   |          Auto Running number          |
|   4.  |                 Document No.                 |              Document No.             |
|   5.  |                 Document Date                |            Date on Document           |
|   6.  |                 Document Type                | Type of Document refer to RD standard |
|   7.  |                 Total Amount                 |           Amount include VAT          |
|   8.  |                 Generate Date                |        Date/Time of import data       |
|   9.  |                    Source                    |            Source of input            |
|  10.  |                 Review Status                |        Status of Review Invoice       |

<mark style="color:green;">Column description of Screen Review Invoice</mark>

[^1]: 
