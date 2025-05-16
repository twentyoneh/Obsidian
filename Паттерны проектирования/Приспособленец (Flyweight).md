Шаблон нужен когда нам нужно создать много однотипных объектов эти объекты должны быть максимально облегчёнными
![[Pasted image 20250516122116.png]]

```cpp
class	TreeModel
{
private:
		Mesh	mesh_;
		Texture	bark_;
		Texture	leaves_;
};
```

```cpp
class	Tree
{
private:
		TreeModel*	model_;
		Vector	position_;
		double	height_;
		double	thickness_;
		Color	barkTint_;
		Color	leafTint_;
};
```

![[Pasted image 20250516124558.png]]

```cpp
class	World
{
public:
		World()
		:	grassTerrain_(1,	false,	GRASS_TEXTURE),
			hillTerrain_(3,	false,	HILL_TEXTURE),
			riverTerrain_(2,	true,	RIVER_TEXTURE)
		{}
private:
		Terrain	grassTerrain_;
		Terrain	hillTerrain_;
		Terrain	riverTerrain_;
		//	Другие	вещи...
};
```

```cpp
void	World::generateTerrain()
{
		//	Заполняем	землю	травой.
		for	(int	x	=	0;	x	<	WIDTH;	x++)	{
				for	(int	y	=	0;	y	<	HEIGHT;	y++)	{
						//	Добавляем	немного	холмиков.
						if	(random(10)	==	0)	{
								tiles_[x][y]	=	&hillTerrain_;
						}	else	{
								tiles_[x][y]	=	&grassTerrain_;
						}
				}
		}
		//	Добавляем	рекую
		int	x	=	random(WIDTH);
		for	(int	y	=	0;	y	<	HEIGHT;	y++)	{
				tiles_[x][y]	=	&riverTerrain_;
		}
}
```
