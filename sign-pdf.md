# Sign PDF

You can utilize the "getInvoice" system to apply digital signatures to PDF files. To import the PDF files, you must provide a Control File in CSV format. The Control File should contain specific columns, which are described in detail in the table below.

**Table** ‎: Description of filling in the control file

| Column            | Explanation                                                         |
| ----------------- | ------------------------------------------------------------------- |
| PDF\_NAME         | The name of the PDF file to be imported into the getInvoice system. |
| DOCUMENT\_TYPE    | Document type                                                       |
| DOCUMENT\_NO      | Document number                                                     |
| DOCUMENT\_DATE    | Date of issue                                                       |
| SELLER\_EMAIL     | Seller's email                                                      |
| SELLER\_TELEPHONE | Seller's phone number                                               |
| BUYER\_NAME       | Buyer's name                                                        |
| BUYER\_EMAIL      | Buyer's email                                                       |
| BUYER\_TELEPHONE  | Buyer's phone number                                                |
| PDF\_PATH         | Path for storing PDF documents on zDOX                              |
| OUTPUT\_FILENAME  | File name of the PDF document stored on zDOX or SFTP.               |

You can upload PDF files and Control File attachments to designated channels. For the PDF file, its name should only match the information in the PDF\_NAME column (Shown icon ![](<.gitbook/assets/image (130).png>)). If the uploaded PDF file name does not match the information in the PDF\_NAME column, an icon will be displayed  ![](<.gitbook/assets/image (98).png>).

<figure><img src=".gitbook/assets/image (122).png" alt=""><figcaption><p>Example of placing PDF files and Control Files</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (66).png" alt=""><figcaption><p>Jobs screen - PDF file successfully imported.</p></figcaption></figure>

You can click to view transactions.

<figure><img src=".gitbook/assets/image (124).png" alt=""><figcaption><p>Jobs Screen – View Transactions</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (127).png" alt=""><figcaption><p>Jobs screen - Failed to import PDF file</p></figcaption></figure>

You can click to view an error detail of transactions.

<figure><img src=".gitbook/assets/image (117).png" alt=""><figcaption><p>Jobs – View Error Information of Transactions.</p></figcaption></figure>
