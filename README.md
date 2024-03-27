# Funciones en SQL


<br />
<br />

## 1. Ejemplo


```sql
create or alter function DiferenciaHora(
@Var1 datetime,
@Var2 datetime
)
returns varchar(50)
	begin
		declare @Otro varchar(50)
		set @Otro = case when @Var2 >= dateadd(minute, -4, @Var1) and @Var2 <= @Var1 then 'Si'
					else 'No' end
	return @Otro
	end
go
```

<br />
<br />

## 2. Ejemplo

```sql
create or alter function FunContador(
@Var1 nvarchar(100),
@Var2 nvarchar(100)
)
returns int
	begin
		declare @Otro int
		set @Otro = case when @Var1 is null then 0
					else count(*) over(partition by @Var1 order by @Var2) end
	return @Otro
	end
go
```


