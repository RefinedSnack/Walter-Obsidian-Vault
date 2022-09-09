# Milestone_1

```plantuml
skinparam linetype ortho
skinparam linecorner round
skinparam linetype polyline


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
}


User "*" ----> "*" User : follows >
User "1  " --> "1  " Feed
Feed "*" o-- "*" Status 
User "1" --> "  1" Story
User "1  " -- "*" Status : < authored by 
User "*" <-- "*" Status : mentions
Story "1" *-- "*" Status

```





