#!/bin/bash
set -x
function usage {
    echo  "Usage: 
	$0 [wordpress_site] [backup_path]
	wordpress_site - path to your  WordPress site for backup it (e.g. /var/www/site.com )
	backup_path - destination for your backups (e.g. /backup  )
	";
	exit 1
}
if [ $# -lt 2 ]; then usage; fi

wp_src=${1%/}
bcp_dst=${2%/}

db_pass=`cat "$wp_src"/wp-config.php|grep DB_PASSWORD|awk -F \' '{print $4}'`
db_src=`cat "$wp_src"/wp-config.php|grep DB_NAME|awk -F \' '{print $4}'`
db_user=`cat "$wp_src"/wp-config.php|grep DB_USER|awk -F \' '{print $4}'`
db_pref=`cat "$wp_src"/wp-config.php|grep table_prefix|awk -F \' '{print $2}'`
db_opts="$db_pref"options
# backup  database
mkdir -p "$bcp_dst"
mysqldump -u$db_user -p$db_pass $db_src|gzip > "$bcp_dst"/"$db_src"-`date +%y%m%d_%H%M`".sql.gz"

wp_domain=`mysql -u$db_user -p$db_pass $db_src -s -N -e "select option_value from  $db_opts  where option_name='home';"|awk -F \/ '{print $3}'`

# backup files
wp_dst="$bcp_dst"/"$wp_domain"-`date +%y%m%d_%H%M`

mkdir -p "$wp_dst"
rsync -a --exclude='wp-content/uploads'  "$wp_src"/ "$wp_dst"/
if [ $? -ne 0 ]; then
	cp -ra "$wp_src"/* "$wp_src"/.htaccess  "$wp_dst"/
fi

echo "Резервное копирование завершено"
ls -lh "$bcp_dst"
du -sh "$wp_dst"
