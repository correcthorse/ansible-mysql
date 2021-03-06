correcthorse.mysql
=========

An ansible role for installing and configuring mysql, mariadb or percona. Please note that some mysql flavors are only for certain versions of RHEL/CentOS. There will be better documentation on this in the future.

Role Variables
--------------
| Variable				| Default			| Notes						|
| :---					| :---				| :---						|
| mysql_flavor				| ''				| '', 'percona', 'mysql-community', 'mysql-ius' |
| mysql_version				|				| 		    	       			|
| mysql_install_client			| false				|						|
| mysql_install_server			| false				|						|
| mysql_install_devel			| false				|						|
| mysql_create_once			| false				| turn on run_once for user/permission creation |
| mysql_root_user			| root				| built-in 'root' will be removed if not root	|
| mysql_root_password			| password			|						|
| mysql_host				| localhost			|						|
| mysql_port				| 3306				|						|
| mysql_open_port			| false				|						|
| mysql_bind_address			| "0.0.0.0"			|						|
| mysql_key_buffer_size			| '16M'				|						|
| mysql_max_allowed_packet		| '4M'				|						|
| mysql_thread_stack			| '256K'			|						|
| mysql_thread_cache_size		| 9				|						|
| mysql_myisam_recover			| 'BACKUP'			|						|
| mysql_max_connections			| 151				|						|
| mysql_table_open_cache		| 2048				|						|
| mysql_query_cache_type		| 0				|						|
| mysql_query_cache_limit		| '1M'				|						|
| mysql_query_cache_size		| '16M'				|						|
| mysql_character_set_server		| 'utf8'			|						|
| mysql_collation_server		| 'utf8_unicode_ci'		|						|
| mysql_mysqldump_max_allowed_packet	| '128M'			|						|
| mysql_isamchk_key_buffer		| '16M'				|						|
| mysql_innodb_flush_log_at_trx_commit	| 1				|						|
| mysql_innodb_buffer_pool_size		| '128M'			|						|
| mysql_innodb_lock_wait_timeout	| 50				|						|
| mysql_innodb_log_buffer_size		| '8M'				|						|
| mysql_innodb_log_file_size		| '48M'				|						|
| mysql_innodb_file_per_table		| 'innodb_file_per_table'	| set to empty string to turn this off		|


Notes
------------

If you are not managing a mysql server directly and are creating dbs or database users from a cluster of app nodes, set
mysql_create_once to true so those tasks only run on a single node

Dependencies
------------

- correcthorse.common

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: correcthorse.mysql, mysql_install_client: true, mysql_install_server: true, mysql_flavor: percona }

License
-------

MIT

Author Information
------------------

* [Joshua Rusch](https://correct.horse/)
