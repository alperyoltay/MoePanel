#MoePanel
 Uguu ve Pomf için dosyaları kaldırmayı ve kara listeye almayı kolaylaştıran yönetici paneli.
 
#Özellikler
* Yüklenen dosya sayısı ve kullanılan depolama alanı hakkında bilgiler.
* Karma/dosya adı/vb. tarafından yüklenen dosyaları arayın.
* Dosyaları kara listeye alın veya silin.
* IP ile ilgili tüm dosyaları kara listeye alın veya silin.
* Kara liste veritabanını arayın ve yönetin.

Ayarlar gibi daha fazla özellik daha sonraki bir sürümde gelecektir.
 
# Ekran görüntüsü
<img width="548" alt="Screenshot 2021-07-07 at 19 55 58" src="https://user-images.githubusercontent.com/2499891/124806933-87e7cc80-df5d-11eb-8715-c9bb184b8b8a.png">
<img width="1680" alt="Screenshot 2021-07-07 at 19 55 25" src="https://user-images.githubusercontent.com/2499891/124806958-8dddad80-df5d-11eb-8104-7685fd349f2c.png">
<img width="1678" alt="Screenshot 2021-07-07 at 19 58 39" src="https://user-images.githubusercontent.com/2499891/124807158-c4b3c380-df5d-11eb-873f-57a0e8df5428.png">
<img width="1680" alt="Screenshot 2021-07-07 at 19 55 40" src="https://user-images.githubusercontent.com/2499891/124806978-933af800-df5d-11eb-9e58-ba2202c79aea.png">

#Kurulum
Öncelikle çalışan bir user/Pomf kurulum kurulumuna ihtiyacınız olacak, bundan sonrası oldukça kolay.

**Bazı veritabanı değişiklikleri getirdiğinden bu panelin çalışması için user/Pomf'un en son sürümünü çalıştırmanız gerekir.**

#### projeyi kopyalamak için
```
git clone https://github.com/pomf/moepanel
```

#### moepanel/static/php/settings.inc.php dosyasını düzenleyin
```
<?php

//define('MOE_DB_CONN', 'mysql:unix_socket=/tmp/mysql.sock;dbname=pomf');
define('MOE_DB_CONN', 'sqlite:/path/to/your/uguu/or/pomf/db.sq3');

/**
 * PDO database login credentials
 */

/** @param string POMF_DB_NAME Database username */
define('MOE_DB_USER', null);
/** @param string POMF_DB_PASS Database password */
define('MOE_DB_PASS', null);

/**
 * 'MOE_ROOT' - Root location for the Moe Panel
 * 'FILES_ROOT' - Location where uploaded files for Uguu/Pomf are stored
 * 'PU_NAME' - Pomf/uguu instance name
 * 'PU_ADDRESS' - Pomf/uguu address/[sub]domain
 * 'PU_URL' - URL where Pomf/Uguu serves files from
 * 'MOE_URL' - URL for Moe Panel
 */
define('MOE_ROOT', '/var/www/moepanel/');
define('FILES_ROOT', '/var/www/files/');
define('PU_NAME', 'Uguu');
define('PU_ADDRESS', 'uguu.se');
define('PU_SERVE_URL', 'https://a.uguu.se/');
define('MOE_URL', 'https://moepanel.uguu.se');
```


#### gen_pw.php dosyasını düzenleyin ve YOURPASSWORDHERE'yi istediğiniz bir şifreyle değiştirin.
```
<?php
$lol = password_hash("YOURPASSWORDHERE", PASSWORD_BCRYPT);
echo $lol;
```


#### Daha sonra dosyayı çalıştırın ve çıktıyı kopyalayın.
```
php gen_pw.php
```



#### Başlatmak için
```
cd /path/to/moe
make
```


#### Kullanıcınızı DB'nize ekleyin.
```
sqlite3 /var/www/db/your_pomf_db.sq3
INSERT INTO accounts VALUES(1,'your@email.com','PASSWORD_HASH_FROM_ABOVE',1);
```


**Ardından web sunucunuzu ve PHP'yi dist/'dan hizmet verecek şekilde yapılandırın ve hazırsınız!**

