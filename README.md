# STM_file_management
A set of python scripts to help with the management, conversion and reading of STM data files created by Omicron MATRIX and Vernissage.

# Usage
Load the package and open a flat file.
```
import flatfile_3

ff = flatfile_3.FlatFile(filepath)
```

You can then access the experiment summary
```
ff.experimentInfo
```
or the data directly
```
data = ff.getData()
```
this will return a list of all measurements. To get access to the parameters and raw data within
```
print(data[0].info)
print(data[0].data)
```

# Changing tip configuration
If you run into errors with the above, you are probably using a multitip setup and will need to configure the axis as follows. The numbers after the underscore presumably refer to the tip in use.

```
axes_dict = {
                'V': 'Default_3::Spectroscopy_2::V',
                'X': 'Default_4::XYScanner_4::X',
                'Y': 'Default_4::XYScanner_4::Y',
                }

ff = flatfile_3.FlatFile(filepath, axes_keys=axes_dict)
```
