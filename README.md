# Reverse-Proxy-wordpress-free
Hal-hal yang dibutuhkan:
- WP Hosting:
 -- [FREE] pantheon.io — ga bisa costum domain

- Reverse Proxy
 -- [FREE] Heroku — butuh debit/credit card untuk costum domain
 -- [FREE] Vercel — ga butuh debit/credit card untuk costum domain
 -- [FREE] cloudflare pages — ga butuh debit/credit card untuk costum domain

Step:
0. pastikan sudah login ke akun heroku/varcel/cloudflare pages & pantheon kamu.
1. Silahkan buat wordpress baru pada pantheon.io atau kalau sudah punya web sebelumnya, silahkan migrasi ke pantheon. ada plugin migrasi nya kok, cek https://pantheon.io/docs/migrate/
2. Saat pembuatan / migrasi kamu akan mendapatkan subdomain kira-kira seperti ini -> dev-xxxxxx.pantheonsite.io
3. deploy proxy [heroku/varcel/cloudflare pages]. Menuju ke repo saya https://github.com/tirinfo/Reverse-Proxy-free lalu klik tombol Deploy.
 - App name: isi bebas
 - Region: Bebas
 - Upstream: (subdomain yang kamu dapat dari step 2)
3[heroku/varcel/cloudflare pages].
 - repo saya https://github.com/tirinfo/Reverse-Proxy-free untuk reverse proxy dari pantheon ke saas (heroku/varcel/cloudflare pages)
 - lalu edit pada file "now.json" dan ubah https://dev-wp-tirinfo.pantheonsite.io dengan subdomain yang kamu dapat dari step 2
 - deploy repo yang sudah kamu fork & edit ke saas
4. silahkan login ke wordpress (pantheon) kamu lalu install plugin filemanage (bebas)
5. buka file "wp-config-pantheon.php", "wp-config.php" hapus / komen line terdapat kata-kata
 - define('WP_HOME','xxxx') -> kemungkinan berada pada line 62
 - define('WP_SITEURL','xxxx') -> kemungkinan berada pada line 63
6. di repo saya pada README.md ada potongan codingan di paling bawah, silahkan paste code itu pada file "wp-config-pantheon.php" 
tepat dibawah tag pembuka php (<?php) JANGAN LUPA GANTI wahidin-proxy.herokuapp.com dengan subdomain heroku / domain pribadi kamu.
DEMO 😁:
- pantheon subdomain: https://dev-wp-tirinfo.pantheonsite.io/
- cloudflare pages Reverse Proxy: https://wahidin-proxy.herokuapp.com



for wordpress reverse proxy, open your wp-config.php. after PHP tag opening at the beginning of the file, add these lines of code:

```html
define('PROXY_DOMAIN', 'reverse-proxy-wordpress-free.pages.dev'); //change it to your proxy domain without http/s & slash (/) at the end!
define('.COOKIE_DOMAIN.', PROXY_DOMAIN);
define('.SITECOOKIEPATH.', '.');
if(isset($_SERVER['HTTP_X_FORWARDED_FOR'])) $_SERVER['REMOTE_ADDR'] = explode(',',$_SERVER['HTTP_X_FORWARDED_FOR'])[0];
$_SERVER['HTTP_HOST'] = PROXY_DOMAIN;
$_SERVER['REMOTE_ADDR'] = 'https://'.PROXY_DOMAIN;
$_SERVER[ 'SERVER_ADDR' ] = PROXY_DOMAIN;
if ($_SERVER['HTTP_X_FORWARDED_PROTO'] == 'https') $_SERVER['HTTPS']='on';
define('WP_HOME', 'https://'.PROXY_DOMAIN);
define('WP_SITEURL', 'https://'.PROXY_DOMAIN);
```
