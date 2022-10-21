all: results/01.txt

DB_URL=http://15445.courses.cs.cmu.edu/fall2017/files/md_courts.dump.gz

# Download a compressed SQLite database dump
db.gz:
	wget -O db.gz ${DB_URL}

db.sqlite3: db.gz
	zcat db.gz | sqlite3 db.sqlite3

results/01.txt: query/01.sql db.sqlite3
	sqlite3 db.sqlite3 <query/01.sql  >results/01.txt

makefile.png: Makefile
	makefile2dot | dot -Tpng > makefile.png
