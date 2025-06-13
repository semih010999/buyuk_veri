Bu proje, Counter-Strike 2 (CS2) oyununda aimbot hilelerini makine öğrenimi teknikleri kullanarak tespit etmeyi amaçlamaktadır. Proje, oyuncuların nişangah hareketlerindeki insan dışı davranışları incelemeyi hedefliyor.
Çalışmada "CSGO Cheating Dataset" adlı veri seti kullanılmıştır; bu set 10.000 normal ve 2.000 hileli oyuncu verisi içerir. Veri seti, oyuncunun yatay/dikey dönüş açıları (AttackerDeltaYaw, AttackerDeltaPitch), nişangahın hedefe uzaklığı (CrosshairToVictimYaw, CrosshairToVictimPitch) ve ateş etme durumu (Firing) gibi özellikleri barındırır. Veri setindeki dengesiz sınıf dağılımı (daha az hileli oyuncu) "sınıf ağırlıkları" (class weights) yöntemiyle dengelenmiştir.
Hile tespiti için Random Forest, LSTM (Long Short-Term Memory) ve XGBoost olmak üzere üç farklı makine öğrenimi ve derin öğrenme algoritması kullanılmıştır. Bu modeller, Random Forest'ın açıklanabilirliği ve aşırı öğrenmeye dayanıklılığı, LSTM'in zaman serileri performansı ve XGBoost'un yüksek doğruluk ve hız yetenekleri nedeniyle tercih edilmiştir. Analizler sonucunda en iyi performansın Random Forest modeli ile elde edildiği belirtilmiştir.
Analizler, hileli oyuncuların crosshair hareketlerinin ani sıçramalarla hedefe kilitlendiğini ve kilitlendikten sonra sabit kaldığını, ardından birden çok kez ateş ettiğini göstermiştir. Temiz oyuncuların hareketleri ise daha yumuşak, doğal ve değişkendir; hedefe yavaş yaklaşırlar ve hedefe nişan aldıktan sonra daha bilinçli bir şekilde, genellikle bir kez ateş ederler. Hileli oyuncular, ilk atışı yapmadan önce hedefe çok daha yakın olma eğilimindedir.
Geliştirilen "CS2 Hileci Oyuncu Tahmin Sistemi", oyuncu hareket verilerini analiz ederek hile olma olasılığını yüzdelik bir değerle tahmin etmektedir.
Projenin çıktıları doğrultusunda bazı öneriler sunulmuştur:
•
Oyun Geliştiricileri İçin: Gerçek zamanlı anomali tespiti ve istatistiksel eşik değerleri belirleme.
•
Anti-Hile Sistemleri İçin: Makine öğrenmesi modellerinin sürekli güncellenmesi ve farklı oyuncu seviyelerine göre adapte edilmiş modeller geliştirilmesi.
•
Oyun Topluluğu İçin: Topluluk temelli hile bildirim sistemleri oluşturulması.
Projenin katkıları arasında davranışsal analiz yaklaşımı, makine öğrenmesi entegrasyonu, veri dengeleme ve görsel karşılaştırmalar yer almaktadır. İlerideki çalışmalar için ise transfer öğrenmesi (farklı FPS oyunlarında uygulama), daha karmaşık derin öğrenme modelleri, gerçek zamanlı testler ve çok kanallı veri entegrasyonu (fare/klavye hareketleri, göz takibi gibi ek özellikler) önerilmiştir.
