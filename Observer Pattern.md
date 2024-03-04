---  
share: "true"  
---  
# Observer Pattern  
  
2 core parts  
Observer  
Subject  
  
```plantuml  
Abstract Subject {  
	-List<Observer> observers  
	+attach(Observer)  
	+detatch(Observer)  
	+notify()  
}  
  
Interface Observer {  
	update()  
}  
  
Subject ..r.> Observer  
```  
  
