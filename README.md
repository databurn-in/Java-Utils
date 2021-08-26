# Java-Utils

In this repository, I will keep uploading some Java utility classes that I've developed and used in my Closed Source projects.

## LongList

An `ArrayList` class is not feasible when you have to store a lot of heavy `Object`s in a list. `LongList` class can easily store more than 100,000 elements in the form of an array in a memory-efficient way without compromising too much on read/write speed. The way this works is, it stores all the elements on the disk (secondary storage) and only stores a fixed number of elements (called a "block") into the memory. Every time you are accessing an element in `LongList`, you'll be reading it from the block (which is stored in the memory) and not from the disk. Hence the speed is not compromised. For example, if you have 500,000 elements stored in `LongList` and the block size that you've defined is 1000, then you'll be consuming the memory only for those 1000 elements and the rest of the elements will be on the disk.

### Code example

 - Initialize a `LongList`
```java
/*  
* providing a unique ID to each LongList is required.  
* Block size is optional. default block size is 500.  
* */  
//'Car' is a sample user-defined class
LongList<Car> carLongList = new LongList<>("car-list", 1000);  
```
 - Add an element to `LongList`
```java
carLongList.add(new Car());
```

- Initialize a `LongList` with an `ArrayList`
```java
carLongList.initialize(carArrayList); 
```
- Access elements from `LongList`
```java
for(int i=0; i<carLongList.size(); i++){ 	
	System.out.println(carLongList.get(i));  
}
```
- Data stored in `LongList` is persistent. To clear the data from a `LongList`
```java
carLongList.clear(); 
``` 
This can also be done like this:
```java
LongList.clear("car-list");
``` 
- You can choose where you want `LongList` to store the data on disk. You can provide the path like this:
```java
// getCacheDir() gives you the cache directory in Android
LongList.storageRootDir = getCacheDir().toString();   
```
Current working directory is the default path where the `LongList` will store the data.


## ObjectStore

This class stores Java Objects on the disk. Uses LRUMap internally. I created this utility class to display 'Recently viewed TV shows' list shown below.

<img height="500" src="https://raw.githubusercontent.com/NandanDesai/res/master/usage-of-objectstore.png">

## License 

Copyright 2021 Nandan Desai

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
