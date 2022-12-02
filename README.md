# Convert Excel Files to CSV with OIC + Oracle Functions

This repository hosts the code required to setup an Oracle Function that will convert Excel files from xlsx and xls format to CSV. It also stores the artefacts required to create an Oracle Integration (OIC) flow that will call this function to perform Excel to CSV file conversions. 

This code is accompanied by a blog article, available here: 
- https://redthunder.blog/2021/10/05/process-excel-files-with-oic-oracle-functions/

Demo video available here:

https://objectstorage.ap-sydney-1.oraclecloud.com/p/VvDdVVBcP4qV4OWBJeJR8OCmIjX6phMIhfrWhrngJ2nltEH-CnADBbkEgyZ7Zwcn/n/sdc90vkxb5rj/b/stv_bucket-20211005-2230/o/Excel2CSV.mp4 

**Function Artefacts**

- [requirements.txt](requirements.txt) specifies the dependencies of the Excel2CSV conversion function
- [func.yaml](func.yaml) contains metadata about the function and declares associated properties
- [func.py](func.py) contains the Python function that converts a single Excel file to a CSV

*Credit for the above code goes to Steven Lawton*

sample file to call the function:
- [request.json](request.json)

to invoke the above function store the sample request in your function folder within Cloud Shell and run:

  `fn invoke stv_FN_Demo convertexcelfiles < request.json`
  
 Limitation: 
 - Multiple worksheets are not supported. Function will only read the first worksheet

**Oracle Integration (OIC) Artefacts**

- [EXCELDEMO_PART1_01.00.0003.iar](EXCELDEMO_PART1_01.00.0003.iar) contains a sample integration that will invoke the above function 
- [CSV_example_1000.csv](CSV_example_1000.csv) is used in the above integration to define the schema for the stage read operation

Sample files: 

Feel free to replace these with anything you like but update the stage read schema definition in the integration:
- [XLS_example_1000.xls](XLS_example_1000.xls) & [XLSX_example_1000.xlsx](XLSX_example_1000.xlsx)


**Note: This code is only intended to be used for demonstration purposes to showcase the capabilities of OIC and related OCI services**
