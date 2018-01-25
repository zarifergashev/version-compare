Version Compare
=====
Lightweight Android library to compare version strings.

This library allows you to compare version strings easily. The version number can follow the SemVer convention but this library will also compare
more than 3 parts (e.g. 1.0.1.22). Additionally common pre-release suffixes are supported.

Pure Java (java.util), no dependencies, very small method count.

## Usage
**A release on jcenter will follow soon.**

To compare two version strings just create a new Version object. Invalid inputs will by default be handled as `0.0.0`. So a valid version string
will always be higher in this case. 
```java
Version exampleVersion = new Version("1.0.2-rc2");

boolean updateAvailable = exampleVersion.isLowerThan("1.0.2"); // updateAvailable = true
```
### Supported pre-release labels
| order | label     |
| ----- | --------- |
| 4     | *empty* or *unknown* |
| 3     | rc        |
| 2     | beta      |
| 1     | alpha     |
| 0     | pre + alpha |


**Note:**

higher order means higher version 1.0 > 1.0-beta

pre-releases versions are supported 1.0-rc3 > 1.0-rc2


### Functions Overview
**Constructor**
* public `Version(String versionString)`
* public `Version(String versionString, boolean throwExceptions)` -> throws exceptions when versionString is *null* or doesn't start with a number

**Getter**
* public int `getMajor()` -> returns major version, default 0
* public int `getMinor()` -> returns minor version, default 0
* public int `getPatch()` -> returns patch version, default 0
* public List< Integer > `getSubversionNumbers()` -> returns list with all numeric version parts found, default empty
* public String `getSuffix()` -> returns suffix (first non-numeric part), default empty
* public String `getOriginalString()` -> returns the initial string

**Compare**
* public boolean `isHigherThan(String otherVersion)`
* public boolean `isHigherThan(Version otherVersion)`
* public boolean `isLowerThan(String otherVersion)`
* public boolean `isLowerThan(Version otherVersion)`
* public boolean `isEqual(String otherVersion)`
* public boolean `isEqual(Version otherVersion)`

## Sample App
![Image](https://raw.githubusercontent.com/G00fY2/version-compare/gh-pages/images/version_compare_sampleapp_framed.png)

## License
	Copyright (C) 2018 Thomas Wirth

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
