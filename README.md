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


## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Author

* **Russ Berg** -  russ.berg@lightsource.ca



## License

This project is licensed under the GPL2 License - see the [LICENSE.md](LICENSE.md) file for details







