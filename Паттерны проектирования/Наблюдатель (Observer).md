обсервер как таковой не со
надо прочитать ещё раз!
при изменении одного объекта все зависящие от него оповещаются об этом и автоматически обновляются 
```cpp
class	Observer
{
public:
		virtual	~Observer()	{}
		virtual	void	onNotify(const	Entity&	entity,	Event	event)	=	0;
};
```

```cpp
class	Achievements	:	public	Observer
{
public:
		virtual	void	onNotify(const	Entity&	entity,	Event	event)	{
				switch	(event)	{
				case	EVENT_ENTITY_FELL:
						if	(entity.isHero()	&&	heroIsOnBridge_)	{
								unlock(ACHIEVEMENT_FELL_OFF_BRIDGE);
						}
						break;
				//	Обработка	остальных	событий	и	обновление	heroIsOnBridge_...
				}
		}
private:
		void	unlock(Achievement	achievement)	{
				//	Разблокирование	если	не	было	разблокировано	раньше...
		}
		bool	heroIsOnBridge_;
};
```