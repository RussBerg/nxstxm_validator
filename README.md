# NXstxm_validator
This is a file structure validator for files that are exported targeting the NEXUS NXstxm application definition
http://download.nexusformat.org/sphinx/classes/applications/NXstxm.html
This validator depends on nexpy to provide the base class and application definitions which are
found in:
    
    <python dist>/Lib/site-packages/nexpy/definitions/base_classes
    <python dist>/Lib/site-packages/nexpy/definitions/applications
    
 Tested with:
* Python 3.7

### Prerequisites

The pyStxm software is dependent on the following python modules (note that their individual dependencies are not listed):

 - h5py (2.6.0)
 - NeXpy (0.9.3)
 - nexusformat (0.4.5)
 - numpy (1.11.3)
 - simplejson (3.10.0)
 - xmltodict (0.12.0)

 

### Installing

Start by creating a clone of the repo:

1. Create a directory to clone the repo

```C:\tmp\Feb21>git clone https://github.com/RussBerg/nxstxm_validator.git```

This will create a **nxstxm_validator** directory with all of the software in it.


## Validating an nxstxm file or all files within a directory 

To validate a single file:

 ```nxstxm_validate(r'-f C:/data/2019/0710/C190710197.hdf5'.split())```
 
 To validate all files within a directory:
 
 ```nxstxm_validate(r'-d C:/data/2019/0710'.split())```

The structure of each entry found in the file will be traversed and a quick check done to make sure that
fields and attributes that are required by the nxstxm definition exist in the file. 
Typical output for a single file looks like this, however the console output will contain some 
colorization to assist in finding issues in a file.



 `````>>> nxstxm_validate(r'-f C:\tmp\aph_jul10\C190710197\C190710197.hdf5'.split())


   Validating nxstxm file [C:\tmp\aph_jul10\C190710197\C190710197.hdf5]:


         ####################################################################
         ### checking for nxentry group called <entry0>:
         ####################################################################
                 > it exists and type=NXentry
                         ### checking <entry0> fields:
                                 field[title] exists and type=NX_CHAR is correct
                                 field[start_time] exists and type=NX_DATE_TIME is correct
                                 field[end_time] exists and type=NX_DATE_TIME is correct
                                 field[definition] exists and type=NX_CHAR is correct
                         ### checking <entry0> groups:
                                 NX_class[NXcollection] > EXISTS but it is OPTIONAL
                                 NX_class[NXmonitor] > it exists
                                 NX_class[NXdata] > it exists
                                 NX_class[NXinstrument] > it exists
                                 NX_class[NXsample] > it exists

         ### checking for NXcollection group
         found NXcollection group called <collection>
                 > it exists and type=NXcollection
                         ### checking <collection> fields:
                                 field[scan_request] exists and type=NXscanDefinition is correct

         ### checking OPTIONAL NXmonitor group called <control>:
                 > it exists and type=NXmonitor
                         ### checking <control> attributes:
                                 attr[axes] > it exists
                                 attr[energy] has a corresponding datagroup in this group
                                 attr[sample_y] has a corresponding datagroup in this group
                                 attr[sample_x] has a corresponding datagroup in this group
                                 attr[signal] > it exists
                                 attr[data] has a corresponding datagroup in this group
                         ### checking <control> fields:
                                 field[data] exists and type=NX_NUMBER is correct
                                 field[energy] exists and type=NX_FLOAT is correct
                                 field[epu_offset] exists and type=NX_FLOAT is correct
                                 field[epu_polarization] exists and type=NX_FLOAT is correct
                                 field[sample_x] exists and type=NX_FLOAT is correct
                                 field[sample_y] exists and type=NX_FLOAT is correct

         ### checking for NXdata group called <counter0>:
                 > it exists and type=NXdata
                         ### checking <counter0> attributes:
                                 attr[axes] > it exists
                                 attr[energy] has a corresponding datagroup in this group
                                 attr[sample_y] has a corresponding datagroup in this group
                                 attr[sample_x] has a corresponding datagroup in this group
                                 attr[axes] > it exists
                                 attr[energy] has a corresponding datagroup in this group
                                 attr[sample_y] has a corresponding datagroup in this group
                                 attr[sample_x] has a corresponding datagroup in this group
                                 attr[signal] > it exists
                                 attr[data] has a corresponding datagroup in this group
                         ### checking <counter0> fields:
                                 field[stxm_scan_type] exists and type=NX_CHAR is correct
                                 field[data] exists and type=NX_NUMBER is correct
                                 field[energy] exists and type=NX_FLOAT is correct
                                 field[sample_y] exists and type=NX_FLOAT is correct
                                 field[sample_x] exists and type=NX_FLOAT is correct
                         ### checking <counter0> stxm_scan_type:
                                 stxm_scan_type = <sample image stack> is a valid type

         ### checking for NXinstrument group called <instrument>:
                 > it exists and type=NXinstrument
                         ### checking <instrument> fields:
                                 field[monochromator] exists and type=NXmonochromator is correct
                                 field[sample_x] exists and type=NXdetector is correct
                                 field[sample_y] exists and type=NXdetector is correct
                                 field[sample_z] > DOES NOT EXIST but it is optional
                                 field[source] exists and type=NXsource is correct
                 ### checking for NXsource group called <source>:
                         > it exists and type=NXsource
                                 ### checking <source> fields:
                                 field[type] exists and type=NX_CHAR is correct
                                 field[name] exists and type=NX_CHAR is correct
                                 field[probe] exists and type=NX_CHAR is correct

         ### checking for NXsample group called <sample>:
                 > it exists and type=NXsample
                         ### checking <sample> fields:
                                 field[rotation_angle] exists and type=NX_FLOAT is correct
File: C:\tmp\aph_jul10\C190710197\C190710197.hdf5 contains a valid nxstxm structure

Done
 `````
 
 In the event that there are errors they will be displayed as they are found as well as the offending file(s) 
 will be listed at the completion of the validation process, similar to this:
 
 ```` There were some errors, the following files contain invalid nxstxm structures  
  [S:\STXM-data\Cryo-STXM\2019\guest\0622\C190622005.hdf5] FAILED nxstxm validation  
  [S:\STXM-data\Cryo-STXM\2019\guest\0622\C190622003.hdf5] FAILED nxstxm validation  
  [S:\STXM-data\Cryo-STXM\2019\guest\0622\C190622004.hdf5] FAILED nxstxm validation  
  [S:\STXM-data\Cryo-STXM\2019\guest\0622\C190622002.hdf5] FAILED nxstxm validation  
 ```` 

## Author

* **Russ Berg** -  russ.berg@lightsource.ca



## License

This project is licensed under the GPL2 License - see the [LICENSE.md](LICENSE.md) file for details







