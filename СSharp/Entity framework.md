1-ое что нужно сделать - это создать объект, который будет олицетворять базу данных.
``` cs
[Table("Users")]
public class User
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    public Guid Id { get; set; }
    public int UserId { get; set; }
    public string? Username { get; set; }
    public int MessageCount { get; set; } = 0;
    public string LastActive { get; set; } = "none";
    public string DateStartSubscription { get; set; } = "none";
    public string DateEndSubscription { get; set; } = "none";
    public string SubscriptionStatus { get; set; } = "free";
}
```
Чтобы работать с этой сущностью через Entity Framework, лучше всего создать класс контекста, который наследует от `DbContext`, и определить в нём `DbSet<User>`
Контекст - это прослойка между БД и классом 

```cs
public class ApplicationDbContext : DbContext
{
    public ApplicationDbContext(DbContextOptions<ApplicationDbContext> options)
        : base(options)
    {
    }

    public DbSet<User> Users { get; set; }

    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        base.OnModelCreating(modelBuilder);
        // Здесь можно добавить дополнительную конфигурацию модели, если необходимо
    }
}

```


#### SQL == C# (сопоставление типа данных)
- int : int
- bit : bool
- char : string
- date : DateTime
- datetime : DateTime
- datetime2 : DateTime
- decimal : decimal
- float : double
- money : decimal
- nchar : string
- ntext : string
- numeric : decimal
- nvarchar : string
- real : float
- smallint : short
- text : string
- tinyint : byte
- varchar : string
