# NGP6 - Handling missing and zero values

**Proposed by:**&#x20;

**Date:**&#x20;

**Status: Proposed**

### **Context**

Quantitative data uploaded to Wazimap NG takes the format

| Geography | Dimension 1 | Dimension 2 | Dimension n | Count |
| --------- | ----------- | ----------- | ----------- | ----- |
| CPT       | Yellow      | Hot         | ...         | 123   |

Where there could be any number of dimensions (zero to many) which classify the value in Count.

Only categorical values are currently supported well. Time series has been implemented using year-month pairs as categories and ordering the members chronologically.

One dimension is usually used as a main variable, e.g.

* In the Rich Data view, as the categories on the y-axis.
* In the data mapper, as options to toggle between to present different categories on the choropleth.
* In Key Metrics and Profile Highlights, a single category is selected to be the category presented.

The remaining dimensions are offered as filters in the data mapper and rich data view.



### Missing data and zero

Sometimes no data is available for a given geographic area. It is important to present missing data as such, and not assume that missing values are zero. Consider a dataset on vaccinations, where some provinces have submitted their data, some have submitted zero, while others have not submitted any data yet.

| Geography | Vaccine | Count |
| --------- | ------- | ----- |
| EC        | Pfizer  | 123   |
| EC        | JJ      | 234   |
| WC        | Pfizer  | 0     |

Without being told how to interpret missing values, we know

* Eastern Cape has administered 123 Pfizer vaccines
* Eastern Cape has administered 234 JJ vaccines
* Western Cape has administered 0 Pfizer vaccines

We do not know

* How many JJ vaccines the western cape have administered
* How many of any kind of vaccine Limpopo have administered

## **Proposed Solution 1**

### **Benefits**

### **Disadvantages**

## **Proposed Solution 2**

### **Benefits**

### **Disadvantages**

### **Other implications**

## **Proposed Solution 3**

### Benefits

### Disadvantages

## **Resolution**

This problem was finally addressed by ...&#x20;
