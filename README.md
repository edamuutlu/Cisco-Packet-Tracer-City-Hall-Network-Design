**Belediye Binası Ağ Tasarımı**

1. **Proje Tanımı ve Amacı**

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

2. **Uygulanan Teknolojiler**

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


**Önizleme**

![Onizleme](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/94ff60ec-f334-4c4a-af91-66f199d6d80c)

Şekil 1. Uygulama Görünümü



1. **Proje Aşamaları**


A. **Doğru Kablolama ile Ağ Cihazlarının Bağlantılandırılması**

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

)![Kablolama](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/e6e425ab-f78e-4b0e-9857-6d389cfac3cd)

Şekil 2. Uygulamanın Cihaz ve Kablolama Görünümü






B. **Temel Cihaz Ayarlarının Yapılandırılması**

ISP’ler, Multilayer switchler ve core routerların AC Power kablosu ilgili porta takılıp kabloların port durumları (port status) aktif edildi. 

Cihazların CLI kısmından hostname ve şifre isimleri sırasıyla cihaz adı ve “cisco” olacak şekilde atandı. 
![ssh-SW](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/5e35b109-c6b6-436f-a434-d8f4ad1f78c7)
![ssh-ML](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/4081371c-91e0-4497-bc0b-6c442d475775)

Şekil 3 ve 4. Switch ve Multilayer Cihazlarının Yapılandırılması

![ssh-CR](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/755f586e-4921-4c63-9814-7e3b977b976c)

Şekil 5. Router Cihazının Yapılandırılması

C. **VLAN'ların Oluşturulması ve Portlara VLAN Numaralarının Atanması**

![vlan-mhtrlk](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/e776fdab-1345-4128-b2a7-d844f456f280)

Şekil 6. Muhtarlık Departmanında VLAN Oluşturulması

![vlan-yaziisleri](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/d70e6ff0-64e4-4845-a992-036d69cec2bd)

Şekil 7. Yazı İşleri Departmanında VLAN Oluuşturulması

![ML-trunk](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/72696558/f9411b17-3276-4176-ab20-0b248893012b)

Şekil 8. Multilayer Switch Arayüzlerinde Trunk Modunun Açılması

![vlan-ML](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/89240fa1-94c8-431b-b302-dd4c9cb711be)

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


![ML1-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/04b6b590-1ff0-4627-9881-c9850f5c56bb)

Şekil 10. Multilayer Switch1’e IP Ataması

Şekil 10’da Multilayer Switch 1’e Tablo 2’deki network adresi 172.16.3.144 olduğu için 172.16.3.145 ip adresi atandığı görülmektedir. Network adresinin bir fazlası şeklinde diğer ip adreslemeler de tamamlanmaktadır.

![ML2-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/987ddfe6-e9ec-4f95-8d58-048ae196c9d6)

Şekil 11. Multilayer Switch2’ye IP Ataması

![CR1-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/59eb64c9-0dc6-4976-9592-78b1b8b94783)

Şekil 12. Core Router1’e IP Ataması

![CR2-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/044ea70e-a402-4625-8aa2-8652d2c94f5a)

Şekil 13. Core Router2’ye IP Ataması

![ISP1-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/8c643553-6ff2-46c2-ac73-b010bd50210a)

Şekil 14. ISP1’e IP Ataması

![ISP2-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/c8cf6a92-9620-4b79-aa49-a1efadeafe71)

Şekil 15. ISP2’ye IP Ataması

Cisco Packet Tracer'da bir ISP simüle etmek için "Cloud" (Bulut) bileşeni kullanılmaktadır. Bu bileşen, dış ağ kaynaklarına erişim sağlamak için kullanılır ve İnternet Servis Sağlayıcısı (ISP) olarak temsil edilmektedir. Şekil 14 ve 15’ de ISP1 ve ISP2’ye arayüz numaraları dikkate alınarak uygun ip adresleme işlemleri yapılmaktadır.








E. **Routing Protokolü Olarak OSPF'nin Yapılandırılması**

![ML2-Routing](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/707e5239-7ad3-482a-b815-c22c692fb2fc)

Şekil 16. Multilayer Switch2 Routing İşlemleri

![ML1-Routing](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/6c46c8b6-89e0-4474-88ec-381b242a8b10)

Şekil 17. Multilayer Switch1 Routing İşlemleri

![CR1-Routing](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/7ca20850-2753-4595-8d45-0f2cec1ca752)

Şekil 18. Core Router1 Routing İşlemleri

F. **Sunucu Odasındaki Cihazlara Statik IP Adres Atama**

![DHCP-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/19f8f37c-fe7a-4672-b3e6-d2af335fe34d)

Şekil 19. DHCP-Server Statik IP Atama İşlemi

![EMAİL-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/c6e80af1-f809-4dbb-9cf7-8d1590cde25a)

Şekil 20. Email-Server Statik IP Atama İşlemi

![DNS-IP](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/0f0d1fcc-5e62-4e8d-9a52-7a7b004901b8)

Şekil 21. DNS-Server Statik IP Atama İşlemi

Sunucu odasındaki cihazlara statik olarak IP atanmaktadır. Sunucu odasında, sunucuların genellikle önemli bir rolü vardır ve ağda sürekli olarak kullanılabilir olmaları gereklidir. Bu nedenle, sunuculara statik IP adresleri atanır. Statik IP adresleri, cihazlar arasında sabit bir kimlik oluşturur ve bu kimlik, sunucuların ağda her zaman kolayca tanınmasını sağlar.

Alt ağlara bölme işleminde dördüncü kattaki sunucu odasının networkü 192.168.4.128 olarak belirlenmişti. Bu sebeple DHCP-Server, Email-Server ve DNS-Server’a sırasıyla 192.168.4.130, 192.168.4.133, 192.168.4.131 adresleri atanmaktadır. Default gateway adresleri iletişim kurulacak switchin ip adresini belirtmektedir.


G. **DHCP Servis Yapılandırılması ve DNS Servis Domain Name Belirleme**

![DHCP-Servis](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/9feaee49-9122-4edb-9bfe-1f1ba42bc802)

Şekil 22. DHCP-Server Servis İşlemleri

Şekil 21’de DHCP Server içinde DHCP servisi aktif edilerek departmanların pool name, default gateway, dns server, başlangıç ip adresi, subnet mask ve o departmanın alabileceği maksimum kullanıcı sayısının girişi yapılmaktadır. Daha sonra her departmandaki cihazların desktop IP Configuration kısmından static olarak seçilen kısmı DHCP olarak seçilerek dinamik IP atamasını gerçekleştirildi.

![DNS-Servis](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/964b28fe-1b4c-499b-8fb6-be9187fcf0f4)

Şekil 23. DNS-Serverda DNS Servisini Aktif Etme

H. **Multilayer Switchler Üzerindeki Inter-VLAN Yönlendirmenin Yapılandırılması (Anahtar Sanal Arayüzü)**

![ML-InterVlan](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/02070b30-98da-423f-bf29-768048b6dd68)

Şekil 24. Multilayer Switch1 Inter-VLAN Yönlendirmenin Yapılandırılması

Inter VLAN yönlendirmesi, farklı VLAN'larda bulunan cihazlar arasında iletişim kurmak için kullanılan bir tekniktir. VLAN'lar, ağda ayrı ayrı segmentler oluşturarak ağın daha iyi yönetilmesini sağlar. Ancak, VLAN'lar arasında doğrudan iletişim olmadığı için inter VLAN yönlendirmesi gereklidir.

Inter VLAN yönlendirmesi, ağdaki Multilayer Switch1 tarafından gerçekleştirilmektedir. Bu cihazlar, farklı VLAN'lar arasında trafiği yönlendirerek cihazların birbirleriyle iletişim kurmasını sağlar. Bu işlem, paketleri bir VLAN'dan diğerine taşıyarak ve VLAN taglerını kullanarak gerçekleştirilir.

İ. **WLAN veya Kablosuz Ağın Yapılandırılması**

![AP-Ağ](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/5f5b3431-c1b2-4a5c-94ca-f030476cf87b)

Şekil 25. Accesspointer için Kablosuz Ağı İsimlendirme ve Şifreleme

![Wifi-Connect](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/5f62ffa8-0a34-435d-8362-a569a333a4d7)

Şekil 26. Laptopu Kablosuz Ağa Bağlama

WPA2-PSK (Wi-Fi Protected Access 2 with Pre-Shared Key), Wi-Fi ağlarının güvenliğini sağlamak için kullanılan bir şifreleme protokolüdür. WPA2-PSK, ağ trafiğini şifreleyerek, ağa yetkisiz erişimi önlemeye yardımcı olur.

J. **PAT (Port Address Translation) Olarak NAT Overload'un Yapılandırılması**

![CR1-PAT](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/571b8ec1-65d1-450c-933b-7385ba5e535a)

Şekil 27. Core Router1 PAT İşlemleri

![CR2-PAT](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/4525a014-407d-48c7-b94f-772b06fe51ea)

Şekil 28. Core Router2 PAT İşlemleri

PAT yapılandırması için "ip nat inside" ve "ip nat outside" komutlarını kullanarak iç ve dış arayüzleri belirttik. Bu yapılandırma, iç ağdaki bir dizi IP adresini, tek bir IP adresi ve port numarası kombinasyonuyla dış ağa çevirir. Bu sayede iç ağdaki birçok cihazın aynı anda internete erişimi sağlanmış olur.

K. **Ağ İletişimini Test Etme ve Doğrulama**

![ISP1-Ping](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/ef1f277b-8e51-4250-9c03-b50153580720)

Şekil 29.1. ISP1’den Ping Atma Örneği

![ISP2-Ping](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/3bb1a605-74ce-454f-98ee-1b8a5a5499b6)

Şekil 29.2. ISP2’den Ping Atma Örneği

![Deparrtman-Ping](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/e77553d8-a0ee-49ae-9342-4a0161e79bbd)

Şekil 30. ARGEM Departmanından Muhtarlık Departmanına Ping Atma




![Email-1](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/dacdb42b-c80b-4aa3-b216-256b4b2b17d4)
![Email-2](https://github.com/edamuutlu/Cisco-Packet-Tracer-City-Hall-Network-Design/assets/112180102/973691bd-5778-46a7-ad7c-f6dedfc730d6)

Şekil 31.1 ve 32.2. Başarılı Bir Email Gönderim Örneği












4. **Sonuç ve Tartışma**

Bu çalışmada Router, switch, Access pointer, PC, laptop, tablet, printer ve gerekli sunucular içeren bir geniş alan ağı ve yerel alan ağları gerçekleştirilmiştir. Bu ağ topolojisi gerçeklenmesi sırasında Packet Tracer yazılımı kullanılmış ve gerçek Router, switch programlaması ile özdeş cihaz programlaması yapılmıştır. VLANLAR tanımlanmış bu VLANlar gerekli cihazlara konfigüre edilmiştir. PC’ler için sunucu odası haricindeki departmanlara DHCP havuzları tanımlanmış ve PC’lerin IP’leri aldığı gözlemlenmiştir. DNS sunucu tanımlanmıştır ve DHCP havuzları üzerinden PC’lere dağıtılmıştır. EMAİL sunucu tanımlanmış ve erişim gözlemlenmiştir. Hayali bir geniş ağ oluşturularak ISP tanımlanmıştır. Geniş bir ağda ve yerel bir ağda olması gereken temel cihazlar ve protokoller kullanılmıştır. Hem statik hem de dinamik IP konfigürasyonları eş zamanlı simüle edilmiştir. Simülasyon sonuçları ağda herhangi bir paketin kaynak ile hedef arasında problemsiz ulaşabildiği gösterilmiştir.

5. **Kaynakça**

[1] T. Lammle, “CCNA: Cisco certified network associate study guide”, 5th Edition, SYBEX Press, 2003.

[2] D. Barnes, B. Sakandar, “Cisco LAN Switching Fundamentals”, CISCO Press.

[3] <https://www.netacad.com/courses/packet-tracer> (Erişim zamanı: 10.05.2023).
20
