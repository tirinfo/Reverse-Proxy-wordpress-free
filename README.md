# Reverse-Proxy-wordpress-free
Vercel Reverse Proxy wordpress

for wordpress reverse proxy, open your wp-config.php. after PHP tag opening at the beginning of the file, add these lines of code:

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
