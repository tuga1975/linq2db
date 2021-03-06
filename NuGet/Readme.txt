Release notes for newer versions moved to https://github.com/linq2db/linq2db/wiki/Releases-and-Roadmap

LINQ to DB 1.10.1  Release Notes
---------------------------------
- fix async retry policy (#919)
- fix connection management (#927)

- feature: allow to configure null checking in predicates (#932)

- obsoletes: LinqToDB.Configuration.Linq.CheckNullForNotEquals, use CompareNullsAsValues instead


LINQ to DB 1.10.0  Release Notes
---------------------------------
- breaking change: [Oracle] bulk mode property (OracleTools.UseAlternativeBulkCopy) changed type from bool to AlternativeBulkCopy enum. If you assigned it to true, you should replace it with AlternativeBulkCopy.InsertInto value.
- breaking change: [Oracle] Old implementation used TO_DATE literal for DataType.DateTime type and TO_TIMESTAMP literal for other date and time types. New implementation will use TO_TIMESTAMP for DataType.DateTime2 type and TO_DATE for other date and time types (#879)

- documentation: Added XML documentation for mapping functionality (#836)
- documentation: Added documentation on explicit join definition: https://github.com/linq2db/linq2db/wiki/Join-Operators

- feature: LINQ extension methods to define inner and outer (left, right, full) joins (#685)
- feature: [Oracle] New bulk insert mode added (AlternativeBulkCopy.InsertDual) (#878)
- feature: new DataConnection async extensions: ExecuteAsync, ExecuteProcAsync, QueryToListAsync, QueryToArrayAsync (#838)
- feature: [MySQL] BulkCopyOptions.RetrieveSequence support (only for single integer indentity per table) (#866)
- feature: support for query expression preprocessing (#852)

- improvement: added Sql.NoConvert helper function to remove unnecessary conversions, introduced by LINQ (#870). Fixes #722
- improvement: [MS SQL] XML parameters support for SQL Server (#859)
- improvement: joins optimization improvements (#834)
- improvement: expression tests generator improvements (#877)
- improvement: [Informix] return default schema flag and schema name for tables in schema provider (#858)

- fix: [Firebird] regression in string literals support for Firebird < 2.5 (#851). You should set FirebirdConfiguration.IsLiteralEncodingSupported to false for firebird < 2.5
- fix: internal IDataContextEx interface functionality merged into IDataContext interface to allow custom data contexts implementations (#837)
- fix: functions doesn't work in association predicate exptessions (#841)
- fix: query cache ignores changes to query, made by ProcessQuery method (#862)
- fix: group by issues when grouping by date parts (#264, #790)
- fix: some scenarios doesn't work with extension method associations (#833)
- fix: [.net core] SerializableAttribute type redefinition conflict (#839)
- fix: [.net core] Removed strong name from linq2db.core (#867)
- fix: execute query before returning enumerable result to user (#872)
- fix: [PostgreSQL] added result conversion to integer for DatePart function (#882)
- fix: [DB2] fix exception in DB2 schema provider (#880)
- fix: fix potential NRE (#875)
- fix: configuration (#906)
- fix: generating in (#909)

All changes: https://github.com/linq2db/linq2db/milestone/6


LINQ to DB 1.9.0  Release Notes
---------------------------------
- breaking change: [MySql] access to a table using fully-qualified name using schema/owner is not supported anymore. You should update your code to use database name for it (#681)

- feature: async support (#758)
- feature: SQL MERGE support with new Merge API (#686)
- feature: LINQ query cache management (#645)
- feature: associations could be defined using extension methods (#786)
- feature: overrides, typed by resulting type, added for InsertWithIdentity (#774)
- feature: added possibility to provide predicate expression for associations (#753)
- feature: custom aggregate functions support (#73, #353, #679, #699, #775)

- documentation: initial job on API documentation
- documentation: Added XML documentation to major public API and XML documentation file included to nuget package
- documentation: documentation published on github.io: https://linq2db.github.io
- documentation: new Merge API articles added: https://github.com/linq2db/linq2db/wiki/Merge-API

- improvement: performance improvements for multi-threaded environments (#278)
- improvement: [PostgreSQL] DateTimeOffset type mapped to TimeStampTZ by default (#794)
- improvement: [PostgreSQL] Guid type mapped to uuid by default (#804)
- improvement: tables support in extensions (#773, #777)

- fix: regression in queries generation in 1.8.3 (#825)
- fix: Take/Skip/Distinct promoted to main query from joined subquery (#829)
- fix: wrong SQL generated for Contains subqueries with Take/Skip (#329)
- fix: fixed various issues with BinaryAggregateExpression option enabled (#812)
- fix: better support for Nullable<T> parameters in LINQ queries (#820)
- fix: use of function with IQueryable<T> result type in LINQ query could fail (#822)
- fix: use of retry policy fails for SAP HANA and DB for iSeries, if connection string contains credentials (#772)
- fix: call to Count after GroupBy executed on client (#781)
- fix: better support for SQL literals (#200, #668, #686)
- fix: [Informix] support for cultures with non-dot decimal separator (#145)
- fix: DbConnection.ExecuteReader ignores commandBehavior parameter (#801)
- fix: [Firebird, Oracle, MySql, Informix, SAP HANA, DB2] fully-qualified table name generation fixes for various providers (#778)
- fix: [SQLite] schema generation fails when foreign key targets table (#784)
- fix: [SQL Server] Set SkipOnInsert and SkipOnUpdate flags for computed columns in schema provider (#793)

All changes: https://github.com/linq2db/linq2db/milestone/5


LINQ to DB 1.8.3  Release Notes
---------------------------------
[!] Fixed problems with Configuration.Linq.UseBinaryAggregateExpression (#708, #716)
[!] Experimental support for query retry (#736, https://github.com/linq2db/linq2db/blob/master/Tests/Linq/Data/RetryPolicyTest.cs)

Better support for NpgSql 3.2.3 (#714, #715)
Fixed issue with wrong convert optimization (#722)
Fixed join optimization (#728)
Fixed nullable enum mapping edge cases (#726)
Fixed issue with cached query (#737, #738)
Update with OrderBy support (#205, #729)
Changed string trimming for fixed size string columns (trim only spaces) (#727)
Better support for creating tables with Oracle (#731, #750, #723, #724)
Fixed InsertOrUpdate to work as InsertIfNotExists when update fields not specified (all providers) (#100, #732, #746)


LINQ to DB 1.8.2  Release Notes
---------------------------------
[!] Configuration.Linq.UseBinaryAggregateExpression is set to false by default as supposed to be unstable


LINQ to DB 1.8.1  Release Notes
---------------------------------
Fixed issue with !IEnumerable.Contains (#228)
Fixed GROUP BY DateTime.Year (#264, #652)
Fixed query optimization (#269)
Fixed BinaryAggregateExpression (#667)
Fixed nullable enums support (#693)

Improved Npgsql 3.2 support (#665)
Improved JOIN build (#676)
Improved SqlCe support (#695 )

Minor changes (#664 #696)


LINQ to DB 1.8.0  Release Notes
---------------------------------

Added support for Window (Analytic) Functions: https://github.com/linq2db/linq2db/pull/613
Now ObjectDisposedException will be thrown while trying to use disposed IDataContext instance: https://github.com/linq2db/linq2db/issues/445
Added experimental support for big logical expressions optimization: https://github.com/linq2db/linq2db/issues/447
Optimized use of different MappingSchemas: https://github.com/linq2db/linq2db/issues/615
Added CROSS JOIN support
Added support of TAKE hints: https://github.com/linq2db/linq2db/issues/560
Added protection from writing GroupBy queries that lead to unexpected behaviour: https://github.com/linq2db/linq2db/issues/365
MySql: string.Length is now properly returns number of characters instead of size in bytes when used in query: https://github.com/linq2db/linq2db/issues/343
Fluent mapping enchantments (fixed inheritance & changing attributes several times) 

Number of bug fixes and optimizations


LINQ to DB 1.7.6  Release Notes
---------------------------------


What's new in 1.7.6
---------------------

Multi-threading issues fixes
Inner Joins optimizations (Configuration.Linq.OptimizeJoins)
Fixed issues with paths on Linux
F# options support


What's new in 1.0.7.5
---------------------

Added JOIN LATERAL support for PostgreSQL.



What's new in 1.0.7.4
---------------------

SqlServer Guid Identity support.


New Update method overload:

	(
		from p1 in db.Parent
		join p2 in db.Parent on p1.ParentID equals p2.ParentID
		where p1.ParentID < 3
		select new { p1, p2 }
	)
	.Update(q => q.p1, q => new Parent { ParentID = q.p2.ParentID });


New configuration option - LinqToDB.DataProvider.SqlServer.SqlServerConfiguration.GenerateScopeIdentity.


New DataConnection event OnTraceConnection.


PostgreSQL v3+ support.



What's new in 1.0.7.3
---------------------

New DropTable method overload:

	using (var db = new DataConnection())
	{
		var table = db.CreateTable<MyTable>("#TempTable");
		table.DropTable();
	}


New BulkCopy method overload:

	using (var db = new DataConnection())
	{
		var table = db.CreateTable<MyTable>("#TempTable");
		table.BulkCopy(...);
	}


New Merge method overload:

	using (var db = new DataConnection())
	{
		var table = db.CreateTable<MyTable>("#TempTable");
		table.Merge(...);
	}


New LinqToDBConvertException class is thrown for invalid convertion.
