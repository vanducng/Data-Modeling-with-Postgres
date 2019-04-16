
# Error
(nano_degree) MacVanDuc:Project01-Data Modeling with Postgres vanducng$ python create_tables.py 
Traceback (most recent call last):
  File "create_tables.py", line 50, in <module>
    main()
  File "create_tables.py", line 41, in main
    cur, conn = create_database()
  File "create_tables.py", line 13, in create_database
    cur.execute("DROP DATABASE IF EXISTS sparkifydb")
psycopg2.errors.ObjectInUse: database "sparkifydb" is being accessed by other users
DETAIL:  There is 1 other session using the database.

Fixing referred from https://stackoverflow.com/questions/17449420/postgresql-unable-to-drop-database-because-of-some-auto-connections-to-db
    select * from pg_stat_activity where datname = 'sparkifydb';
    SELECT pg_terminate_backend(pg_stat_activity.pid)
    FROM pg_stat_activity
    WHERE pg_stat_activity.datname = 'sparkifydb';
    