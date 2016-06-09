---
layout: post
title:  "Keep your Entity Framework entities clean with EntityTypeConfiguration"
date:   2015-12-01 01:00:00
tags: ['entity-framework', 'entity-type-configuration', 'mapping']
categories: entity-framework entity-type-configuration mapping
---
## What?

* Entity Framework has two ways of mapping an entity class to a database table
	* Attributes
		* Pollutes the classes
		* Avoid using this approach
	* EntityTypeConfiguration
		* Unobtrusive way of mapping
		* Always use this approach

## How?

* Steps
	* Create a mapping class for every entity
		* Inherit from the EntityTypeConfiguration class
		* Configure mapping in the constructor
	* Add all the mapping classes to the DbContext

**Entity**

```csharp
public class Employee
{
    public int Id{ get; set; }
    public string FirstName{ get; set; }
    public string LastName{ get; set; }
    public string Email{ get; set; }
}
```

**Mapping Class**

```csharp
public class EmployeeMap : EntityTypeConfiguration<Employee>
{
    public EmployeeMap()
    {
        ToTable("Employees");

        HasKey(x => x.Id);

        Property(x => x.Id).HasColumnName("Id");
        Property(x => x.FirstName).HasColumnName("FirstName");
        Property(x => x.LastName).HasColumnName("LastName");
        Property(x => x.Email).HasColumnName("Email");
    }
}
```

**DbContext**

```csharp
public class MyDbContext : DbContext
{
    public MyDbContext() : base("ConnectionStringKey")
    {
    }

    protected override void OnModelCreating(DbModelBuilder builder)
    {
        builder
            .Configurations
            .AddFromAssembly(typeof (MyDbContext).Assembly);
        
        base.OnModelCreating(builder);
    }
}
```