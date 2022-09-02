# MusicPlayer

```plantuml
?-> __FavoritesPlayer__ : playFavorites()
activate __FavoritesPlayer__

__FavoritesPlayer__ -> __FavoritesPlayer__ : playSongs(List<String>)
activate __FavoritesPlayer__
loop for each string in favorites
	__FavoritesPlayer__ -> __MusicDatabase__ : getSong(String)
	activate __MusicDatabase__
	__MusicDatabase__ --> __FavoritesPlayer__ : getSong() return
	deactivate __MusicDatabase__
	
	
	__FavoritesPlayer__ -> __FavoritesPlayer__ : PlaySong(Song)
	activate __FavoritesPlayer__
	|||
	deactivate __FavoritesPlayer__
end
|||
deactivate __FavoritesPlayer__
|||
deactivate __FavoritesPlayer__
```
