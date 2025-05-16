Ключевой	мыслью	является	создание объекта,	который	может	порождать	объекты,	похожие	на	себя.	Если	у	вас	есть один	призрак,	вы	можете	с	его	помощью	получить	кучу	призраков.	Если	есть	демон, можно	сделать	больше	демонов.	Любого	монстра	можно	трактовать	как прототипируемого	монстра,	используемого	для	генерации	новых	версий	его	самого.
```cpp
class	Monster
{
public:
		virtual	~Monster()	{}
		virtual	Monster*	clone()	=	0;
		//	Другие	вещи...
};
```

```cpp
class	Ghost	:	public	Monster	
{
public:
		Ghost(int	health,	int	speed)
				:	health_(health),
						speed_(speed)
		{}
		virtual	Monster*	clone()	{
				return	new	Ghost(health_,	speed_);
		}
private:
		int	health_;
		int	speed_;
};
```

Как	только	все	монстры	будут	его	поддерживать,	нам	больше	не	нужен	будет отдельный	класс	спаунер	для	каждого	класса	монстров.	Вместо	этого	мы	обойдемся всего	одним:
```cpp
class	Spawner
{
public:
		Spawner(Monster*	prototype)
				:	prototype_(prototype)
		{}
		Monster*	spawnMonster()	{
				return	prototype_->clone();
		}
private:
		Monster*	prototype_;
};
```

Внутри	себя	он	содержит	монстра,	скрытого	извне,	который	используется	спаунером	в качестве	шаблона	для	штамповки	новых	монстров	ему	подобных.	Получается	нечто наподобие	матки	пчел,	никогда	не	покидающей	своего	улья.
До паттерна:
![[Pasted image 20250516155737.png]]

После паттерна:
![[Pasted image 20250516155705.png]]

Для	создания	спаунера	призраков,	мы	просто	создаем	прототипируемый	экземпляр призрака	и	затем	создаем	спаунер,	который	будет	хранить	этот	прототип:
```cpp
Monster*	ghostPrototype	=	new	Ghost(15,	3);
Spawner*	ghostSpawner	=	new	Spawner(ghostPrototype);
```

