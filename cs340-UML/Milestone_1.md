# Milestone_1

```plantuml
skinparam linetype ortho
skinparam linecorner round
skinparam linetype polyline

class Follow {
	followers : map<string, User>
	followering : map<string, User>
}
class Story {}
class User {
	-name : string
	-alias : string
	-photoID : string 
}
class Feed {}



class Status {
	-timeStamp : int
	-message : string
	-author : string
	+readMessage() 
}



User "0..*  " <--u-- "0..*  " Follow : followers
User "1" ----> "1" Follow : has
User "0..*" <---- "0..*" Follow : following
User "1  " --> "1  " Feed
Feed "0..*" o-- "0..*" Status 
User "1" --> "  1" Story
User "1  " <-- "0..*" Status : authored by
User "0..*" <-- "0..*" Status : mentions
Story "1" *-- "0..*" Status

```





