## Geodatabases  

### Overview  
Welcome to the **ArcPY_GIS_Automation** repository, where I showcase GIS automation projects using ArcPy. This section, **Geodatabases**, contains subfolders for different geodatabases I have worked with, demonstrating my experience in spatial data management, geodatabase creation, and ArcGIS automation.  

### What is a Geodatabase?  
A **geodatabase** is the native data structure for ArcGIS and the primary format for storing, editing, and managing spatial data. Unlike shapefiles, which store data as separate files, geodatabases store spatial data in a structured format, making them more efficient for large-scale GIS projects.  

Key features of geodatabases:  
- **ESRI’s Preferred Spatial Data Format:** The recommended format for storing GIS data.  
- **Stored as Unintelligible Files:** Unlike shapefiles, geodatabase data is stored in a binary format that is not human-readable but can be viewed and managed in ArcGIS Pro’s **Catalog Panel**.  
- **Contains Feature Classes and Feature Datasets:** Organizes spatial data into feature classes (vector data) and feature datasets (grouped spatial data with the same spatial reference).  
- **Default File Format (.gdb):** Every ArcGIS project is supported by a default **File Geodatabase (.gdb)**, which efficiently stores spatial data and supports versioning.  
- **Attribute Domain Creation:** Allows for controlled data entry by assigning predefined values (e.g., dropdown lists) to attribute fields, ensuring data integrity and consistency.  

### Creating a Geodatabase using ArcPy  
The following steps outline how to create a geodatabase using **ArcPy**, demonstrating automation in geospatial workflows:  

1. **Import ArcPy**  
   ```python
   import arcpy
   ```  
   
2. **Set the Workspace**  
   ```python
   arcpy.env.workspace = "C:/GIS_Projects"
   ```  
   
3. **Create a File Geodatabase (.gdb)**  
   ```python
   arcpy.CreateFileGDB_management("C:/GIS_Projects", "MyGeodatabase.gdb")
   ```  

4. **Create a Feature Dataset (any)**  
   ```python
   arcpy.CreateFeatureDataset_management("C:/GIS_Projects/MyGeodatabase.gdb", 
                                         "MyFeatureDataset", 
                                         spatial_reference=arcpy.SpatialReference(4326))
   ```  
*You can download any feature dataset for free from Naturalearth.com*

5. **Create a Feature Class**  
   ```python
   arcpy.CreateFeatureclass_management("C:/GIS_Projects/MyGeodatabase.gdb", 
                                       "Roads", 
                                       "POLYLINE")
   ```  

6. **Define an Attribute Domain (Example: Road Type)**  
   ```python
   arcpy.CreateDomain_management("C:/GIS_Projects/MyGeodatabase.gdb", 
                                 "RoadType", 
                                 "Type of Roads", 
                                 "TEXT", 
                                 "CODED")
   
   # Add domain values
   arcpy.AddCodedValueToDomain_management("C:/GIS_Projects/MyGeodatabase.gdb", 
                                          "RoadType", 
                                          "HWY", 
                                          "Highway")
   arcpy.AddCodedValueToDomain_management("C:/GIS_Projects/MyGeodatabase.gdb", 
                                          "RoadType", 
                                          "ST", 
                                          "Street")
   ```  

### Repository Structure  
This repository contains various geodatabases corresponding to different projects. Within **ArcPY_GIS_Automation/Geodatabases**, I have organized subfolders for each geodatabase I have worked with, including scripts and relevant datasets.  

#### Directory Structure:  
```
ArcPY_GIS_Automation/
│── Geodatabases/
│   ├── Dhaka_GDB/
```  
