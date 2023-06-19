# CTF-Wakanda

-> Makineyi çözmeye ilk olarak netdiscover kullanarak ip sini bularak başlıyoruz

![Ekran Alıntısı1](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/2c616087-97f7-4416-a2ca-22140a411d8d)


-> Sonraki adımda ise nmap taraması yapıyoruz ve nmap sonuçları aşağıdaki gibidir


![Ekran Alıntısı2](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/e12a20b2-5786-497c-8925-4f8068d49a0c)

-> Nmap taraması sonucu 80 portunun açık olduğunu görüyoruz ve 10.0.2.14 sayfasını ziyaret ediyoruz ve sayfa kaynağını inceliyoruz


![Ekran Alıntısı3](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/6cc18268-cc00-4336-a554-4cc0d87d2e7c)

-> Burada ise yorum satırı şeklinde bir modülün yazıldığını görüyoruz ve directory traversal zafiyeti olduğunu keşfediyoruz ve şu kodu ekliyoruz
  "php://filter/convert.base64-encode/resource=index" bu kodu ekledikten sonra bize base64 ile şifrelenmiş bir kod geliyor 
  

![Ekran Alıntısı4](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/d906d298-3cc8-44f4-acfc-2852c1341b81)


-> Gelen bu kodu decode ettikten sonra karşımıza bir kullanıcının passwordu çıkıyor


![Ekran Alıntısı5](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/125d3d9a-6142-428b-9802-3099acfc2c4a)


-> Bu şifre ile ssh bağlantısıyla "mamadou" kullanıcısı olarak bağlanıyoruz


![Ekran Alıntısı6](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/1ef1c5dd-06bf-4d6b-871a-05505c8feab7)


-> Makineye girdiğimizde konsolda temel linux komutlarının çalışmadığını görüyoruz ve sadece python komutlarının çalıştığını fark ediyoruz bundan dolayı "import pty pty.spawn("/bin/bash")"  komutunu kullanarak bir shell açıyoruz.


![Ekran Alıntısı7](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/ec372136-cb4d-4f39-971e-4b32658bdb50)


-> Mamadou kullanıcısı olarak ilk flagımızı alıyoruz 


![Ekran Alıntısı8](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/580360bf-bae1-4888-bace-e4f57479fb73)


-> Sonrasında diğer flaglarımızdan biri olan flag2 yi almak için ise flag2.txt nin olduğu dosya konumuna gidip almayı deniyoruz fakat yetkimizin olmadığını görüyoruz 


![Ekran Alıntısı10](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/0a850de7-46b5-400f-8e34-9bea69cee2fb)


-> Bu flagı alabilmek için devops kullanıcısı olmamız gerektiğini fark ediyoruz ve devops kullanıcısına ait dosyaları arıyoruz bunun sonucunuda bir tane dosya dikkatimizi çekiyor 


![Ekran Alıntısı11](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/07c76d80-2379-409e-ba6f-1dc5ae7c6c7d)


-> Bulduğumuz bu dosya ile reverse shell almaya çalışıyoruz ve bu dosyanın içeriğini düzenliyoruz 


![Ekran Alıntısı12](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/7da2b64d-fcb6-4811-9332-52453a944a04)


-> Reverse shellimizi yazdıktan sonra nc ile dinlemeye alarak bu python dosyasını çalıştırıyoruz ve devops kullanıcına ait shellimizi ve aynı zamanda flag2yide alıyoruz


![Ekran Alıntısı13](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/3536d6e8-d953-4211-a8a4-48ffdddc3d59)


-> Geriye root olmak kaldı bunun için ise "sudo -l" komutunu çalıştırarak devops kullanıcısı olarak root yetkisine sahip hangi dosyaları çalıştırabileceğimizi buluyoruz bu dosyalardan birinin ise "/usr/bin/pip" komutu olduğunu görüyoruz ve "https://github.com/0x00-0x00/FakePip" bu adresten FakePip adlı dosyayı çektikten sonra "setup.py" dosyasında bazı düzenlemeler yapıyoruz 


![Ekran Alıntısı14](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/8bb25aa0-59e6-439e-99cb-655c41656220)


-> Son aşama olarak nc ile dinleme yaptıktan sonra "setup.py" dosyasını çalıştırıyoruz ve root olarak son flagımızıda alıyoruz


![Ekran Alıntısı15](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/7a8e1caa-7c45-4b82-bd37-8400de5e7793)



























