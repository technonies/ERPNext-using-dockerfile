# ERPNext-Installation-within-docker-

Credentials: 
MARIADB_ROOT_PASSWORD=12345
mariadb-root-username=root
Admin user=administrator
Admin password=321


-------------------------------------------------------
STEP-1: PULL
  --> docker pull technonies/erpnextdb
	--> docker pull technonies/erpnext

STEP-2: RUN
	--> docker run --detach --network mynet --name mariadbb  --env MARIADB_ROOT_PASSWORD=12345 -v <path-of-conf-file>:/etc/mysql/mariadb.conf.d  technonies/erpnextdb
	--> docker run -it -d  --network mynet --name erp -p 8000:8000 -p 9000:9000 -p3306:3306  technonies/erpnext
	
STEP-3: EXEC in technonies/erpnext
	--> bench new-site <www.site.com> --admin-password '321' --mariadb-root-username root  --db-host mariadbb
	--> bench --site <www.site.com> install-app erpnext
	--> cd /home/frappe/bench/sites && echo '<www.site.com>' >currentsite.txt
	--> cd /home/frappe/bench && bench start

