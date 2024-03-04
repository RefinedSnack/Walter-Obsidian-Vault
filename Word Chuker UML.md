---  
share: "true"  
---  
# Word Chuker UML  
  
  
```plantuml  
  
class UserInput {  
	+ Selected files  
	+ Input directory  
	+ Output directory  
}  
  
class Configurations {  
	+ Every selected option  
	+ Input directory  
	+ Output directory  
	+ Saved between launches of the program  
}  
  
class GUI {  
	+ Advanced options  
	+ Select input folder  
	+ Select specific files  
	+ Select output folder  
}  
  
class GenerateDatabase {  
	+ Intput: file  
	+ Output: Database object  
	+ Should be multithreaded  
}  
  
class Database {  
	+ Contains stored info for each word  
	+ Contains chunk bondaries  
	+ Contains counts by word for each file  
}  
  
class Word {  
	+ String raw (this is the word as it originally appeared)  
	+ String root (this is the word stripped of puntuation and capitalization)  
	+ Index  
}  
  
class LeadingContents {  
	+ String contents  
	+ Index  
}  
  
class Chunk {  
	+ parent file name  
	+ chunk id  
}  
  
```  
