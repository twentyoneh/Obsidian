```cs
		Score = 0;
        TowerManager = new TowerManager();
        GameStateManager = new GameStateManager();
        EnemyManager = new EnemyManager();
        DifficultyManager = new DifficultyManager();
        SpriteManager = new SpriteManager();
        Player = new Player(100);
        var citadelPosition = new Vector2(graphicsDevice.Viewport.Width / 2, graphicsDevice.Viewport.Height / 2);
        var citadel = new Citadel(Guid.NewGuid(), citadelPosition, 100, 10, 200f, TimeSpan.Zero);
        CitadelManager = new CitadelManager(citadel);
```
