# STM_file_management
A set of python scripts to help with the management, conversion and reading of STM data files created by Omicron MATRIX and Vernissage.

# Install
Clone the repository and run the following from within the cloned directory
```
pip install -e .\
```

# Usage
Load the package and open a flat file.
```
from mtrx.flatFile import FlatFile

ff = FlatFile(filepath)
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

ff = FlatFile(filepath, axes_keys=axes_dict)
```

# File conversion (MATRIX -> FFF)
Ensure that Vernissage is installed on the computer you intend to run this on, then set the it's path
```
import mtrx.toFlat as mtrx2flat

mtrx2flat.set_vernissagecmd_path('C:\\Program Files\\Scienta Omicron\\Vernissage\\V2.4.1\\Bin\\VernissageCmd.exe')
```

You can then convert all .mtrx files in a certain folder to flat files painlessly
```
# matrix file directory
input_dir = './20190528'
# flat file directory
output_dir = './20190528-output'

mtrx2flat.convert(input_dir, output_dir)
```
