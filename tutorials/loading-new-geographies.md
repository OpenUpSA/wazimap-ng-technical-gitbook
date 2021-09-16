# Loading new geographies

Here is a quick tutorial for loading up new geography files into Wazimap. To start you need your boundaries in ESRI Shapefile format. In this example, I am going to upload 2011 Wards.

I downloaded the shapefiles from the Municipal Demarcation Board website and loaded them up into QGIS. Here is what the wards look like:

![](../.gitbook/assets/1.-wards.png)

￼

Each layer needs to have four fields:

**Name** - The common name of the boundary, e.g. Western. Cape

**Code** - A unique identifier, this can be anything but it is best if it is a commonly used identifier such as ISO3166 for countries

**Parent\_cod** \(this is due to the field length limitation in shapefiles\) - The code of the parent Geography.  This field can be blank if it is a top-level geography such as a country. ESRI shapefiles limit field names to 10 letters which is why this is truncated.

**Area** - This field has been included for historic reasons and will likely be dropped in future.

Back to QGIS, we inspect our attribute table. The above-mentioned fields need to be added. We can also see that wards do not have a parent geography. Extraneously fields such as **OBJECTID**, **WARNo**, etc need to be removed.

![](../.gitbook/assets/2.-attribute-menu.png)

![](../.gitbook/assets/3.-attribute-table.png)

All the fields except for **PklWardID** are extraneous. We will remove them now.

First, make sure that you select the toggle editing option in the **Layer menu**

![](../.gitbook/assets/4.-toggle-editing.png)

Now select the delete option and remove all of the unnecessary fields.

![](../.gitbook/assets/5.-delete-button.png)



![](../.gitbook/assets/6.-delete-dialogue.png)

You will be left with only one field which is the ward code. Wards do not have a separate name and so we will use the **code** as the **name**. We will use the field calculator to create both **name** and **code** fields.

![](../.gitbook/assets/7.-field-calculator.png)

Here is an example of what the dialogue box should look like:

![](../.gitbook/assets/8.-field-calculator-dialogue.png)

Do the same for code.

The attribute table show now look like this:

![](../.gitbook/assets/9.-attribute-table.png)

Now we can delete the **PklWardID** field as before.

The next field to create Is Area. We can use the field calculator area function to do this. $area is given as square meters, divide by a million to get square kilometres.

![](../.gitbook/assets/10.-attribute-table-area.png)

You will note that we do not have a parent geography as an attribute. This is required by Wazimap in order to create geography hierarchies. We can use the **Join Attributes by Location** tool until the **Vector -&gt; Data** **Management** **Tools** menu. We load up another layer which contains the parent geographies and then use the tool to run a spatial join between the two layers. The tool will then create a copy of our Ward layer with the desired code field from the parent layer. In this case, our parent layer is municipalities.

![](../.gitbook/assets/11.-add-layer.png)

![](../.gitbook/assets/12.-add-layer.png)

A quick look at the municipalities layer’s attribute table shows the following:

![](../.gitbook/assets/13.-mn-attribute-table.png)

In this case, the code column with be used as **parent\_cod** of the wards.

Run the **Join Attributes by Location** tool with the following settings:

![](../.gitbook/assets/14.-join-attributes-dialogue.png)

In brief, the input layer represents the child layer, i.e. wards, the join layer is the parent layer, i.e. municipalities. I choose to join based on wards that are are within municipalities. I also ticked the **intersects** box because there are some tiny overlaps between wards and municipalities in my shapefiles. You will need to check that this does what you expect. 

Once you click run, it will create a new layer with the fields that we want. Note that on my computer, this dialogue is occasionally displayed behind the main QGIS window. Keep this in mind if your dialogue disappears.

The attribute table of the new layer now contains the parent code in the **code\_2** column.

![](../.gitbook/assets/15.-new-attribute-table.png)

All that’s left is to create a new Parent\_cod column by copying the value from code\_2 and then deleting code\_2 \(unfortunately it isn’t possible to rename the column\). 

### **Simplifying boundary files**

The file produced in the previous step was 122mb. Before loading boundaries into Wazimap, I use mapshaper.org to compress them by removing unnecessary detail. 

![](../.gitbook/assets/16.-mapshaper.png)

When importing, be sure to import all of the various files associated with the shapefile, i.e. **wards.shp**, **wards.dbf**, **wards.prj**, and any other files that are provided. Also, tick the **snap vertices** checkbox to ensure that almost identical points are snapped together.

![](../.gitbook/assets/17.-mapshaper-import.png)

Now select simplify from the top-right menu. Accept the default options or experiment with the settings to get the best results.

![](../.gitbook/assets/18.-mapshaper-simplify-map.png)

You are presented with a slider which you can use to decide what level of simplification you are happy with.

![](../.gitbook/assets/19.-mapshaper-slider.png)

Too much simplification results in strange shapes

![](../.gitbook/assets/20.-mapshaper-too-much-simplification.png)

To choose an appropriate trade-off between file size and detail, I typically zoom into the smallest boundary that I expect the user to be interested in and simplify until it becomes unrecognizable, then I dial it back a little. In this case, I simplified to 11.2%. Once I export the file again as a shapefile, it has been reduced to 16mb.

### Loading shapefiles into Wazimap

To load the file into Wazimap you will now need to run the **loadshp** management command

`python3 manage.py loadshp /tmp/wards.shp code=code,name=name,parent_cod=parent_code,area=area ward "2011 Boundaries"`

**/tmp/wards.shp**  - path to the shapefile I exported from map shaper

**code=code,name=name,parent\_cod=parent\_code,area=area ward** - a mapping between the attribute names in the shapefile and the expected field names, in this case they are almost identical as we gave the attributes the correct names in QGIS.

**ward** - a label for the type of geography

**"2011 Boundaries"** - This is the label \(version\) for the geography hierarchy that the boundaries belong to.

When importing, the script will look for the parent geography found in the **parent\_cod** field with the same version. If the parent is not found the geography will not be loaded. Geographies without values in **parent\_cod** are considered to be root Geographies.

### Creating a Geography Hierarchy 

You can load multiple shapefiles in the previous step to create a hierarchy of linked geographies. In order to use these geographies, you need to create a **GeographyHierarchy.** You can find the dialogue here: **/admin/datasets/geographyhierarchy/add/**. 

### Creating a profile

You will need to create a new profile that uses this hierarchy. A tutorial to do this can be found [here](creating-a-new-profile.md).  Your new profile will need to also define how geographies will be displayed. Below is an example configuration for the profile. In this case `preferred_children` provide instructions for which geography levels will be displayed when multiple options exist.  


```text
{
  "urls": [
    "beta.youthexplorer.org.za",
    "localhost"
  ],
  "preferred_children": {
    "country": [
      "province"
    ],
    "district": [
      "municipality",
      "mainplace",
      "ward"
    ],
    "province": [
      "district",
      "municipality"
    ],
    "mainplace": [
      "subplace"
    ],
    "municipality": [
      "mainplace",
      "ward"
    ]
  }
}
```

### Loading datasets

All datasets that are loaded will need to be associated with this **GeographyHierarchy** in order to use with your profile. Data files that are uploaded will need a **Geography** column that uses the same codes as those in your shapefiles in order to join correctly. 

An explanation of the most important classes and how they relate to Datasets can be found [here](../system-architecture/database-models.md).

