Tutor Wordpress gratis!!! - Lumayan buat web pribadi bang heheh 😃
Hal-hal yang dibutuhkan:
- WP Hosting:
 -- [FREE] pantheon.io — ga bisa costum domain 🙁
- Reverse Proxy
 -- [FREE] Heroku — butuh debit/credit card untuk costum domain 🙃
 -- [FREE] Vercel — ga butuh debit/credit card untuk costum domain 😉
Step:
0. pastikan sudah login ke akun heroku/varcel & pantheon kamu.
1. Silahkan buat wordpress baru pada pantheon.io atau kalau sudah punya web sebelumnya, silahkan migrasi ke pantheon. ada plugin migrasi nya kok, cek https://pantheon.io/docs/migrate/
2. Saat pembuatan / migrasi kamu akan mendapatkan subdomain kira-kira seperti ini -> dev-xxxxxx.pantheonsite.io
3[heroku]. Menuju ke repo saya https://github.com/izulwahidin/Heroku-Reverse-Proxy lalu klik tombol Deploy to heroku.
 - App name: isi bebas
 - Region: Bebas
 - Upstream: (subdomain yang kamu dapat dari step 2)
3[vercel].
 - silahkan fork repo saya https://github.com/izulwahidin/Vercel-Reverse-Proxy
 - lalu edit pada file "now.json" dan ubah https://dev-wahidin.pantheonsite.io dengan subdomain yang kamu dapat dari step 2
 - deploy repo yang sudah kamu fork & edit ke vercel
4. silahkan login ke wordpress (pantheon) kamu lalu install plugin filemanage (bebas)
5. buka file "wp-config-pantheon.php" hapus / komen line terdapat kata-kata
 - define('WP_HOME','xxxx') -> kemungkinan berada pada line 62
 - define('WP_SITEURL','xxxx') -> kemungkinan berada pada line 63
6. di repo saya pada README.md ada potongan codingan silahkan paste code itu pada file "wp-config-pantheon.php" tepat dibawah tag pembuka php (<?php) JANGAN LUPA GANTI wahidin-proxy.herokuapp.com dengan subdomain heroku / domain pribadi kamu.
DEMO 😁:
- pantheon subdomain: https://dev-wahidin.pantheonsite.io/
- Heroku Reverse Proxy: https://wahidin-proxy.herokuapp.com/ -> ga costum domain soalnya akun saya belum verified :v
- vercel: https://blog.wahidin.eu.org/
