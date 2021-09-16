# NGP1 - Changing the data model \(Implemented\)

## **NG Proposal 1 - Changing data model**

**Proposed by: Adi Eyal**

**Date: 2020-08-31**

**Status: Proposed**

### **Context**

The data model that NG has been built around is the concept of a universe, i.e. the total number of people in a particular context. This universe can then be disaggregated by a number of attributes. For instance the country population is a universe that is divided into male and female, i.e.:

**`# male + # female = total population`**  


**Similarly:**

**`# Left-handers in WC + # Right-handers in WC = total population of WC`**  


The input file might look like this:  
  
****

| **Geography** | **Preferred hand** | **Count** |
| :--- | :--- | :--- |
| **Western Cape** | **Left** | **30** |
| **Western Cape** | **Right** | **50** |
| **Eastern Cape** | **Left** | **80** |
| **Eastern Cape** | **Right** | **95** |

**Table 1**  


That works well for census data where you are disaggregating a universe. It falls short when you would like to compare two unrelated datasets side-by-side. As an example:  
  
****

| **Geography** | **Access to drinking water** | **Year** | **Count** |
| :--- | :--- | :--- | :--- |
| **Western Cape** | **Have access to drinking water** | **2016** | **30,000** |
| **Western Cape** | **Have access to drinking water** | **2017** | **35,000** |

**Table 2**  


In this case, we cannot sum the two rows to get the universe, i.e. there aren’t 30,000 + 35,000 = 65,000 people with access to water in the Western Cape. We do however ever want to be able to compare these two figures.   


The problem does not only apply to time-based data, e.g.  
  
****

| **Geography** | **Age Group** | **Employment Status** | **Count** |
| :--- | :--- | :--- | :--- |
| **Western Cape** | **15-24** | **Employed** | **40,000** |
| **Western Cape** | **12-24** | **Unemployed** | **60,000** |
| **Western Cape** | **15-35** | **Employed** | **80,000** |
| **Western Cape** | **15-35** | **Unemployed** | **120,000** |

**Table 3**

In this case we have two universes which overlap but we still want to be able to compare them:  
****

![](https://lh4.googleusercontent.com/iL4gI7ssYKmHq-sorLAn4y9NR6Aa2bC50M-6fW0SUJ7dgUJMjdxi6h_XfLZ1s5gZ7GGNkdlbLi-ZSb7BHqXYEJULoIEpBYGimLTjOLyIKwhccZ9KfbbRHfaoFBx0jsUDI7J5JFUM)

## **Proposed Solution 1**

An underlying assumption of the dataset model is that there is only one count field in every file. We could change this assumption by allowing multiple counts, effectively pivoting our table.  
  
****

| **Geography** | **Access to drinking water** | **Year - 2016** | **Year - 2017** |
| :--- | :--- | :--- | :--- |
| **Western Cape** | **Have access to drinking water** | **30,000** | **35,000** |

Table 4  


This solution will require significant changes to the following components:  


* Data Import
* Variable Creation \(data is aggregated at this level\)
* API
* Front-end data model
* Front-end visualisations

We would also need to decide how the system would identify count columns. The current convention is to match by name. We could use a similar approach by requiring a standard prefix, e.g. Count: 2016. Alternatively, the administrator could identify these columns once the data has been uploaded.  


An alternative approach would be to designate a pivot column, e.g. Year.   
****

### **Benefits**

* This is a robust approach that ensures compatibility between Count columns \(compared with Solution 2 below\). Every column available for the first Count column will be available to the second one.

### **Disadvantages**

* A significant amount of effort is required to make this change.
* It limits comparisons of datasets to those that were included in the initial upload. If data from a new year becomes available, it is not possible to include it.
* Depending on implementation, may place an additional burden on the Data Administrator requiring a special naming of columns in the spreadsheet to be uploaded.

### **Proposed Solution 2**

Using this approach we add the concept of a super indicator which ties together two or more indicators together. For instance, table 3 becomes two separate indicators:  
  
****

| **Geography** | **Age Group** | **Employment Status** | **Count** |
| :--- | :--- | :--- | :--- |
| **Western Cape** | **15-24** | **Employed** | **40,000** |
| **Western Cape** | **12-24** | **Unemployed** | **60,000** |

**Table 5**

| **Geography** | **Age Group** | **Employment Status** | **Count** |
| :--- | :--- | :--- | :--- |
| **Western Cape** | **15-35** | **Employed** | **80,000** |
| **Western Cape** | **15-35** | **Unemployed** | **120,000** |

**Table 6**  
  
These are then associated in the backend.

This solution would affect the following components:

* A new database model would be required
* The API will need to be changed
* Front-end data model
* Front-end visualisations

### **Benefits**

* Overall fewer changes are necessary to implement this feature
* Data Administrators are able to associate arbitrary indicators without pre-planning.
* An almost identical workflow is used as the current approach.

### **Disadvantages**

* It is possible to bind two, completely unrelated or incompatible indicators. For instance, the number of bankruptcies vs Child pregnancies.
* Less extreme but equally problematic is two related datasets with different groups, e.g. 2016 Matric passes disaggregated by gender vs 2017 Matric passes without disaggregation. In this case, we will need to decide how this will be displayed on the frontend, especially in graph filters

**In the case of two incompatible datasets, we need to decide whether filters are available for missing groups.**  


![](https://lh5.googleusercontent.com/zfcFBFZ8H_JfxZnqsypJfpfWtLyR9jg6-ybsF0TgleSuN8dKXNbktIzQNcXthvaIaNU9j2--WFNoEpnPR0aA-PY4QIY2usR-bZMpiim-6ud5cuvlMLvf31_YZP7gACk8cAvrPu26)

### **Other implications**

Whereas indicators can now be mapped using a choropleth. Superindicators cannot since a choropleth can only display one Count variable at a time. This can be addressed by another select box allowing the user to choose the Count variable of interest or mapping multi-count variables could be prevented entirely.  


![](https://lh3.googleusercontent.com/q1EzzSboYGpybn0E3VkqFSIQeuvHrkyOq-qKsZ8zE525yZXbvPMaD17SFFl--0cSPNVNosIJoL0rB39a5lNhTsBk9NbpgmdLhP7QPCBCI7uKp7CIttRd1V8bYm2FI15jrioBF_Rw)

## **Proposed Solution 3**

Another  approach to addressing this issue is to recognise that the cause of this problem is the concept of a non-overlapping universe introduce by the **Dataset** model. This approach does not always make sense as in the examples above. To create an **Indicator**, a background process is fired that groups **DatasetData** objects appropriately. In cases like the ones described here, it might be easier to create the indicator directly and avoid datasets entirely.

When creating a new indicator, the admin is asked whether it should be created from a dataset \(the current process\) or whether it should be uploaded from a file. This latter approach would simply create the relevant **IndicatorData** directly. Since an indicator must link to a dataset, one can be created automatically. Creating new indicators from this dataset should not be allowed however.

### Benefits

This is by far the easiest approach to implement. Very little needs to change with the exception of the file upload mechanism when creating a new indicator. Once the IndicatorData objects are created, downstream users of this data remain unchanged. 

It also allows flexibility for data administrators to shape data without too many constraints on the format. 

### Disadvantages

Data re-use is limited. Datasets provide opportunities to create multiple indicators. The superindicator concept allows even more mixing and matching of indicators. 

## **Resolution**

This problem was finally addressed by marking columns as aggregatable or not aggregateable. If a column is not aggregateable, different values in that column need to be shown separately. This can be implemented as a dropdown filter, e.g. you always need to choose a year. Alternatively, a grouped bar chart could be used, e.g. 2016 and 2017 bars. 

The change also involved removing all aggregation from the backend and sending raw data to the frontend.  


