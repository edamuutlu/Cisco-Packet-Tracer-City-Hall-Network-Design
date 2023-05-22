*Belediye Binası Ağ Tasarımı*

1. *Proje Tanımı ve Amacı*

Bir belediye binasında, 855 personel istihdam edilmektedir. Son zamanlarda genişledikleri için yeni bir binaya taşınmaları gerekmektedir. Bir bina belirlendiği ancak ağı olmadığı için yeni binada tasarlanıp uygulanacak yeni bir ağ hizmetine ihtiyaç duyulmaktadır. Yeni bina dört katlı olacak ve her birinde iki departman olacaktır:

1. Birinci kat - (Muhtarlık İşleri-120 kullanıcı beklenmektedir, Yazı İşleri-120 kullanıcı beklenmektedir).
1. İkinci kat - (Kültür İşleri-120 kullanıcı beklenmektedir, Kentsel Dönüşüm-120 kullanıcı beklenmektedir).
1. Üçüncü kat - (Strateji Geliştirme (ARGEM)-120 kullanıcı beklenmektedir, Temizlik İşleri-120 cihaz beklenmektedir).
1. Dördüncü kat - (Bilgi İşlemleri-120 kullanıcı beklenmektedir, Sunucu Odası-15 cihaz beklenmektedir).

Belediye binasının mevcut iş ihtiyacını karşılayan ve geleceğe yönelik hazır bir ağın mantıksal tasarımı gerekmektedir. Bunun için uygulanan adımlar özetle şu şekilde sıralanabilir:

- Cisco Packet Tracer kullanarak ağ çözümünü tasarlanacak ve uygulanacaktır. 
- Her katman için yedeklilik sağlayan hiyerarşik model kullanılacak, yani yedeklilik sağlamak için iki router ve iki multilayer switchin kullanılması beklenecektir. 
- Ağ, ayrıca yedeklilik sağlamak için en az iki ISP'ye bağlanılacak ve her router iki ISP'ye bağlanılacaktır. 
- Her departmanın kullanıcıları için kablosuz ağa ihtiyacı vardır. 
- Her departman farklı bir VLAN'da ve farklı bir alt ağda olacaktır. 
- 192.168.1.0 temel ağı sağlanmış olup, her departmana doğru IP adresi sayısını tahsis etmek için alt ağlar kullanılacaktır. 
- Belediye ağı, iki ISP’ye bağlı 195.136.17.0/30, 195.136.17.4/30, 195.136.17.8/30 ve 195.136.17.12/30 public IP adreslerine (Internet Protocol) bağlıdır. 
- Temel cihaz ayarları, temel cihaz adları, konsol şifreleri, etkin şifreler, banner mesajları, IP etki alanı arama işlemlerini devre dışı bırakma gibi temel cihaz ayarları yapılandırılacaktır. 
- Tüm bölümlerdeki cihazların, ilgili multilayer switchler aracılığıyla birbirleriyle iletişim kurması gerekecektir. 
- Multilayer switchler, hem yönlendirme hem de anahtarlamayı gerçekleştirmesi beklenmektedir, bu nedenle bunlara IP adresleri atanacaktır. 
- Ağdaki tüm cihazların özel DHCP sunucularından dinamik olarak bir IP adresi alması beklenir. 
- Sunucu odasındaki cihazlara IP adresi statik olarak atanacaktır. 
- Routing protokolü olarak OSPF kullanılacak ve rotaları hem yönlendiricilerde hem de multilayer switchler üzerinden tanıtılacaktır.
- Uzaktan oturum açma için tüm yönlendiricilerde ve üçüncü katman anahtarlarında SSH yapılandırılacaktır. 
- PAT'ı, ilgili çıkış yönlendirici arayüzü IPv4 adresini kullanacak şekilde yapılandırılacak ve gerekli ACL kuralını uygulanacaktır. 
- Multilayer switchler ve core routerlara IP routing (yönlendirme) işlemleri yapılacaktır.
- Tüm yapılandırmaların beklenildiği gibi çalıştığından emin olmak için iletişimi test edilecektir.

2. *Uygulanan Teknolojiler*

- Cisco Packet Tracer Kullanarak Bir Ağ Topolojisi Oluşturma.
- Hiyerarşik Ağ Tasarımı.
- Doğru Kablolama ile Ağ Cihazlarının Bağlantılandırılması.
- Temel Cihaz Ayarlarının Yapılandırılması.
- VLAN'ların Oluşturulması ve Portlara VLAN Numaralarının Atanması.
- Alt Ağlara Bölme ve IP Adresleme İşlemleri.
- Multilayer Switchler Üzerindeki Inter-VLAN Yönlendirmenin Yapılandırılması (Anahtar Sanal Arayüzü).
- Dinamik IP Ataması Yapmak İçin Özel DHCP Sunucu Cihazının Yapılandırılması.
- Güvenli Uzak Erişim İçin SSH Yapılandırılması.
- Routing Protokolü Olarak OSPF'nin Yapılandırılması.
- PAT Olarak NAT Overload'un Yapılandırılması.
- WLAN veya Kablosuz Ağın Yapılandırılması (Cisco Erişim Noktası).
- Ana Bilgisayar Cihazı Yapılandırmaları.
- ISP Yönlendiricilerinin Yapılandırılması.
- Multilayer Switch ve Routerlara IP Routing (Yönlendirme) Yapılması
- Ağ İletişimini Test Etme ve Doğrulama. 


*Önizleme*

![Onizleme](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/4a2121a3-9616-4a6d-a163-f8495903ddbb)


Şekil 1. Uygulama Görünümü



1. *Proje Aşamaları*


A. *Doğru Kablolama ile Ağ Cihazlarının Bağlantılandırılması*

**Cisco Packet Tracer uygulamasında kullanılan cihazlar:** 

- İnternet servis sağlayıcı (ISP) olarak görevlendirilen 2 router,
- ISP ile iletişim yollarını yönlendiren 2 adet merkezi (core) router,
- Core router ile departmanlardaki switchlerle iletişimi yönlendirmek üzere görevlendirilen 2 adet multilayer switch,
- Her katta bulunan iki departman için 2 switch kullanılmak üzere toplamda 8 adet switch,
- Her kattaki departmanlarda bir adet PC, bir adet printer, bir adet Access pointer, bir adet laptop ve bir adet tablet kullanılmıştır.

**Cihazlar arasında kullanılan kablo tipleri:**

- ISP ve core routerlar arasında serial DCE kablo tipi kullanılmıştır.
- Core router ve multilayer switch arasında copper straight-through tipi kablo kullanılmıştır.
- Multilayer switch ve departmanlardaki switchler arasında copper cross-over tipi kablo kullanılmıştır.

![Kablolama](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/cfa7e438-a7e6-48c9-a9ab-3129d22e01a2)

Şekil 2. Uygulamanın Cihaz ve Kablolama Görünümü






B. *Temel Cihaz Ayarlarının Yapılandırılması*

ISP’ler, Multilayer switchler ve core routerların AC Power kablosu ilgili porta takılıp kabloların port durumları (port status) aktif edildi. 

Cihazların CLI kısmından hostname ve şifre isimleri sırasıyla cihaz adı ve “cisco” olacak şekilde atandı. 

![ssh-SW](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/35716d22-ef9e-4d8d-8ad7-f949fd1f1773)
![ssh-ML](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/a3576d69-ed82-4f00-a3c4-fb38219fc2b0)

Şekil 3 ve 4. Switch ve Multilayer Cihazlarının Yapılandırılması

![ssh-CR](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/6f26240d-046f-4cf6-b27a-146ca523bc09)

Şekil 5. Router Cihazının Yapılandırılması

C. *VLAN'ların Oluşturulması ve Portlara VLAN Numaralarının Atanması*

![vlan-mhtrlk](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/6c7dbd2a-e761-414c-8704-18852fa2eb5f)

Şekil 6. Muhtarlık Departmanında VLAN Oluşturulması

![vlan-yaziisleri](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/7cbfe8b5-bb9c-4a23-ad25-3eccf7521caf)

Şekil 7. Yazı İşleri Departmanında VLAN Oluuşturulması

![ML-trunk](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/f9411b17-3276-4176-ab20-0b248893012b)

Şekil 8. Multilayer Switch Arayüzlerinde Trunk Modunun Açılması

![vlan-ML](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/111052a0-18e6-4325-a646-8a4ddebc2a6a)

Şekil 9. Multilayer Switchlerine VLAN Tanımlaması

Şekil 6 ve 7’de her departmandaki switch’e vlan tanımlanması görülmektedir. Bu adımdan sonra Multilayer1 ve 2 de trunk modu açılıp departmanların vlan isimleri ve numaraları atanmaktadır.

D. *Alt Ağlara Bölme ve IP Adresleme İşlemleri*

Ağdaki tüm cihazların, sunucu kökünde bulunan özel DHCP sunucularından dinamik olarak bir IP adresi alması beklenmektedir. Ancak sunucu odasındaki cihazlara statik olarak IP adresi atanmaktadır.  Base Network: 192.168.1.0

*İlk Kat*

|*Müdürlükler|Network Adresi|Subnet Mask|Host Adres Aralığı|Broadcast Adresi*|
| :-: | :-: | :-: | :-: | :-: |
|Muhtarlık İşlemleri|192\.168.1.0|255\.255.255.128/25|<p>192\.168.1.1 –</p><p>192\.168.1.126</p>|192\.168.1.127|
|Yazı İşleri|192\.168.1.128|255\.255.255.128/25|<p>192\.168.1.129 –</p><p>192\.168.1.254</p>|192\.168.1.255|

*İkinci Kat*

|*Müdürlükler|Network Adresi|Subnet Mask|Host Adres Aralığı|Broadcast Adresi*|
| :-: | :-: | :-: | :-: | :-: |
|Kültür İşleri|192\.168.2.0|255\.255.255.128/25|<p>192\.168.2.1 –</p><p>192\.168.2.126</p>|192\.168.2.127|
|Kentsel Dönüşüm|192\.168.2.128|255\.255.255.128/25|<p>192\.168.2.129 –</p><p>192\.168.2.254</p>|192\.168.2.255|

*Üçüncü Kat*

|*Müdürlükler|Network Adresi|Subnet Mask|Host Adres Aralığı|Broadcast Adresi*|
| :-: | :-: | :-: | :-: | :-: |
|Strateji Geliştirme (ARGEM)|192\.168.3.0|255\.255.255.128/25|<p>192\.168.3.1 –</p><p>192\.168.3.126</p>|192\.168.3.127|
|Temizlik İşleri|192\.168.3.128|255\.255.255.128/25|<p>192\.168.3.129 –</p><p>192\.168.3.254</p>|192\.168.3.255|

*Dördüncü Kat*

|*Müdürlükler|Network Adresi|Subnet Mask|Host Adres Aralığı|Broadcast Adresi*|
| :-: | :-: | :-: | :-: | :-: |
|Bilgi İşlemleri|192\.168.4.0|255\.255.255.128/25|<p>192\.168.4.1 –</p><p>192\.168.4.126</p>|192\.168.4.127|
|Sunucu Odası |192\.168.4.128|255\.255.255.240/28|<p>192\.168.4.129 –</p><p>192\.168.4.145</p>|192\.168.4.146|

Tablo 1. Alt Ağlara Bölme ve IP Adresleme İşlemleri

*Dördüncü Katman Switchleri (Multilayer Switch) ve Core Routerlar Arası IP Adresleme*


|*Müdürlükler|Network Adresi|Subnet Mask|Host Adres Aralığı|Broadcast Adresi*|
| :-: | :-: | :-: | :-: | :-: |
|R1 – MLSW1|172\.16.3.144|255\.255.255.252|<p>172\.16.3.145 –</p><p>172\.16.3.146</p>|172\.16.3.147|
|R1 – MLSW2|172\.16.3.148|255\.255.255.252|<p>172\.16.3.149 –</p><p>172\.16.3.150</p>|172\.16.3.151|
|R2 – MLSW1|172\.16.3.152|255\.255.255.252|<p>172\.16.3.153 –</p><p>172\.16.3.154</p>|172\.16.3.155|
|R2 – MLSW2|172\.16.3.156|255\.255.255.252|<p>172\.16.3.157 –</p><p>172\.16.3.158</p>|172\.16.3.159|

Tablo 2. Multilayer Switch ve Router Arası IP Adresleme İşlemleri

*Core Router ve ISP’ler Arası IP Adresleme*

Public IP adres :

- 195.136.17.0/30
- 195.136.17.4/30
- 195.136.17.8/30
- 195.136.17.12/30



![ML1-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/4ede10e5-b9e6-4c8c-9273-9b96e81e80fb)

Şekil 10. Multilayer Switch1’e IP Ataması

Şekil 10’da Multilayer Switch 1’e Tablo 2’deki network adresi 172.16.3.144 olduğu için 172.16.3.145 ip adresi atandığı görülmektedir. Network adresinin bir fazlası şeklinde diğer ip adreslemeler de tamamlanmaktadır.

![ML2-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/3d7c44f8-ee7d-4a01-9d82-5983983bbaaf)

Şekil 11. Multilayer Switch2’ye IP Ataması

![CR1-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/7dc5298a-46fe-4963-bd55-d87fb4b73b31)

Şekil 12. Core Router1’e IP Ataması

![CR2-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/1e6903f1-f2c6-4e54-87ce-a42d8ea2afc1)

Şekil 13. Core Router2’ye IP Ataması

![ISP1-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/6bfc346f-0294-4309-85af-726846dadbc6)

Şekil 14. ISP1’e IP Ataması


![ISP2-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/bde31ea6-2851-46cf-8e81-f38169dd7e84)

Şekil 15. ISP2’ye IP Ataması

Cisco Packet Tracer'da bir ISP simüle etmek için "Cloud" (Bulut) bileşeni kullanılmaktadır. Bu bileşen, dış ağ kaynaklarına erişim sağlamak için kullanılır ve İnternet Servis Sağlayıcısı (ISP) olarak temsil edilmektedir. Şekil 14 ve 15’ de ISP1 ve ISP2’ye arayüz numaraları dikkate alınarak uygun ip adresleme işlemleri yapılmaktadır.








E. *Routing Protokolü Olarak OSPF'nin Yapılandırılması*

![ML2-Routing](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/a7bac537-6873-4baf-9d8e-c78b43fdf7cb)

Şekil 16. Multilayer Switch2 Routing İşlemleri

![ML1-Routing](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/5ca27b8a-8cdb-4f1c-b049-df96a8784502)

Şekil 17. Multilayer Switch1 Routing İşlemleri

![CR1-Routing](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/a257ddc0-bd72-4c8c-af19-ccf4663e45f5)

Şekil 18. Core Router1 Routing İşlemleri

F. *Sunucu Odasındaki Cihazlara Statik IP Adres Atama*

![DHCP-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/623356a7-bcde-4aa4-9583-d1fa1f13cd6f)

Şekil 19. DHCP-Server Statik IP Atama İşlemi

![EMAİL-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/ffb0978c-0ec9-44c6-a009-0e2545039b80)

Şekil 20. Email-Server Statik IP Atama İşlemi

![DNS-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/7e314465-7aee-48ac-ac08-5b5f81351685)

Şekil 21. DNS-Server Statik IP Atama İşlemi

Sunucu odasındaki cihazlara statik olarak IP atanmaktadır. Sunucu odasında, sunucuların genellikle önemli bir rolü vardır ve ağda sürekli olarak kullanılabilir olmaları gereklidir. Bu nedenle, sunuculara statik IP adresleri atanır. Statik IP adresleri, cihazlar arasında sabit bir kimlik oluşturur ve bu kimlik, sunucuların ağda her zaman kolayca tanınmasını sağlar.

Alt ağlara bölme işleminde dördüncü kattaki sunucu odasının networkü 192.168.4.128 olarak belirlenmişti. Bu sebeple DHCP-Server, Email-Server ve DNS-Server’a sırasıyla 192.168.4.130, 192.168.4.133, 192.168.4.131 adresleri atanmaktadır. Default gateway adresleri iletişim kurulacak switchin ip adresini belirtmektedir.


G. *DHCP Servis Yapılandırılması ve DNS Servis Domain Name Belirleme*

![DHCP-Servis](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/ae292191-284f-4795-b71f-1028879a5695)

Şekil 22. DHCP-Server Servis İşlemleri

Şekil 21’de DHCP Server içinde DHCP servisi aktif edilerek departmanların pool name, default gateway, dns server, başlangıç ip adresi, subnet mask ve o departmanın alabileceği maksimum kullanıcı sayısının girişi yapılmaktadır. Daha sonra her departmandaki cihazların desktop IP Configuration kısmından static olarak seçilen kısmı DHCP olarak seçilerek dinamik IP atamasını gerçekleştirildi.

![DNS-Servis](https://github.com/edamuutlur/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/47d4a075-a944-4a40-b286-f1eda4692149)

Şekil 23. DNS-Serverda DNS Servisini Aktif Etme

H. *Multilayer Switchler Üzerindeki Inter-VLAN Yönlendirmenin Yapılandırılması (Anahtar Sanal Arayüzü)*

![ML-InterVlan](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/8b0cbfde-b421-4af4-af05-a4865e677c77)

Şekil 24. Multilayer Switch1 Inter-VLAN Yönlendirmenin Yapılandırılması

Inter VLAN yönlendirmesi, farklı VLAN'larda bulunan cihazlar arasında iletişim kurmak için kullanılan bir tekniktir. VLAN'lar, ağda ayrı ayrı segmentler oluşturarak ağın daha iyi yönetilmesini sağlar. Ancak, VLAN'lar arasında doğrudan iletişim olmadığı için inter VLAN yönlendirmesi gereklidir.

Inter VLAN yönlendirmesi, ağdaki Multilayer Switch1 tarafından gerçekleştirilmektedir. Bu cihazlar, farklı VLAN'lar arasında trafiği yönlendirerek cihazların birbirleriyle iletişim kurmasını sağlar. Bu işlem, paketleri bir VLAN'dan diğerine taşıyarak ve VLAN taglerını kullanarak gerçekleştirilir.

İ. *WLAN veya Kablosuz Ağın Yapılandırılması* 

![AP-Ağ](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/1e9307d3-9caf-487c-a038-cc158d879da5)

Şekil 25. Accesspointer için Kablosuz Ağı İsimlendirme ve Şifreleme

![Wifi-Connect](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/860222ab-2f9b-4035-bbb7-067e12deb42f)

Şekil 26. Laptopu Kablosuz Ağa Bağlama

WPA2-PSK (Wi-Fi Protected Access 2 with Pre-Shared Key), Wi-Fi ağlarının güvenliğini sağlamak için kullanılan bir şifreleme protokolüdür. WPA2-PSK, ağ trafiğini şifreleyerek, ağa yetkisiz erişimi önlemeye yardımcı olur.

J. *PAT (Port Address Translation) Olarak NAT Overload'un Yapılandırılması*

![CR1-PAT](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/4d6e3117-8bb4-46e7-b3bc-d79dccf78709)

Şekil 27. Core Router1 PAT İşlemleri

![CR2-PAT](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/6d357047-a4b7-40ba-9d3a-91cbf72c4e14)

Şekil 28. Core Router2 PAT İşlemleri

PAT yapılandırması için "ip nat inside" ve "ip nat outside" komutlarını kullanarak iç ve dış arayüzleri belirttik. Bu yapılandırma, iç ağdaki bir dizi IP adresini, tek bir IP adresi ve port numarası kombinasyonuyla dış ağa çevirir. Bu sayede iç ağdaki birçok cihazın aynı anda internete erişimi sağlanmış olur.

K. *Ağ İletişimini Test Etme ve Doğrulama*

![ISP1-Ping](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/2a567187-c4c9-4c2d-86be-0f021ef6c02c)

Şekil 29.1. ISP1’den Ping Atma Örneği

![ISP2-Ping](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/247bbcf7-c616-41e6-b300-cb2462e7e3a3)

Şekil 29.2. ISP2’den Ping Atma Örneği

![Deparrtman-Ping](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/8bcfe636-a78b-4224-abec-f8f066273cb7)

Şekil 30. ARGEM Departmanından Muhtarlık Departmanına Ping Atma




![Email-1](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/496e163b-eb48-4adf-b9d5-aa1ff290f149)
![Email-2](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/28681a76-1354-4ab2-9afb-be09d02ad450)

Şekil 31.1 ve 32.2. Başarılı Bir Email Gönderim Örneği












4. *Sonuç ve Tartışma*

Bu çalışmada Router, switch, Access pointer, PC, laptop, tablet, printer ve gerekli sunucular içeren bir geniş alan ağı ve yerel alan ağları gerçekleştirilmiştir. Bu ağ topolojisi gerçeklenmesi sırasında Packet Tracer yazılımı kullanılmış ve gerçek Router, switch programlaması ile özdeş cihaz programlaması yapılmıştır. VLANLAR tanımlanmış bu VLANlar gerekli cihazlara konfigüre edilmiştir. PC’ler için sunucu odası haricindeki departmanlara DHCP havuzları tanımlanmış ve PC’lerin IP’leri aldığı gözlemlenmiştir. DNS sunucu tanımlanmıştır ve DHCP havuzları üzerinden PC’lere dağıtılmıştır. EMAİL sunucu tanımlanmış ve erişim gözlemlenmiştir. Hayali bir geniş ağ oluşturularak ISP tanımlanmıştır. Geniş bir ağda ve yerel bir ağda olması gereken temel cihazlar ve protokoller kullanılmıştır. Hem statik hem de dinamik IP konfigürasyonları eş zamanlı simüle edilmiştir. Simülasyon sonuçları ağda herhangi bir paketin kaynak ile hedef arasında problemsiz ulaşabildiği gösterilmiştir.

5. *Kaynakça*

[1] T. Lammle, “CCNA: Cisco certified network associate study guide”, 5th Edition, SYBEX Press, 2003.

[2] D. Barnes, B. Sakandar, “Cisco LAN Switching Fundamentals”, CISCO Press.

[3] <https://www.netacad.com/courses/packet-tracer> (Erişim zamanı: 10.05.2023).
20
