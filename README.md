
Açıklama:

Bu C kodu, bir 8051 mikrodenetleyicisi için tasarlanmıştır (özellikle REG52 varyantı) ve üzerindeki Timer1'i kullanarak Port 0'a bağlı bir tek LED'in hareketini kontrol eder. Ayrıca, Pin P2^0'e bağlı bir basın düğmesinin durumunu izler.

Amaç:

LED Hareketi:

Port 0'daki LED başlangıçta en sağdaki konumuna ayarlanır (lights = 1).
Timer1, kesmeleri üretmek için yapılandırılır ve Timer1 Kesme Servis Rutini'nde (ISR), LED konumu sola kaydırılır (lights = lights << 1). En soldaki LED'e ulaşıldığında (lights == 16), sağdaki konuma sarılır.
Düğme Etkileşimi:

Program sürekli olarak basın düğmesinin durumunu (BUTTON0) izler.
Düğme basılı tutulduğunda (mantıksal düşük), program düğmenin bırakılmasını (mantıksal yüksek) bekler.
Düğme bırakıldığında, LED sola kaydırılır (lights = lights << 1), sol en soldaki LED zaten yanıyorsa sağdaki konuma sıfırlanır (lights = 1).
Düğme debonsmanı için LED hareketinden sonra küçük bir gecikme döngüsü (for (i = 0; i < 1000; i++);) içerir.


Beklenen Davranış:

Port 0'daki LED, Timer1 kesmeleri tarafından kontrol edilen dairesel bir desende sola doğru hareket eder.
Basın düğmesine basmak, LED'i sola kaydıracaktır (sol en soldaki LED zaten yanıyorsa, en sağdaki konuma sıfırlanır).
