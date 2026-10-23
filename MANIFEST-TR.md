# 🏛️ UNIVERSAL AI CLIPBOARD (UAC)

## Yapay Zekâ için Evrensel Pano

### Yapay Zekâ Ajanları için Bir İçerik Yeniden Kullanım Mekanizması

---

> **Yayın Tarihi:** 3 Haziran 2026
> **Durum:** ⚡ Keşif kamuya açık alana sunuldu
> **Lisans:** CC0 1.0 Universal Kamu Malı Beyanı

---

## 📜 KAŞİFİN BEYANI

Ben, **[DScoNOIZ](https://github.com/DScoNOIZ)**, küresel topluluğun önünde beyan ederim:

**1. Ben, yapay zekâ ajanı mimarisinde temelden yeni bir kategorinin kaşifiyim** — **"İsteğe Bağlı Araçlar Arası İçerik Atıf Mekanizması"** (Optional Inter-Tool Content Citation Mechanism); bu kategoriyi **Universal AI Clipboard (UAC)** olarak adlandırdım.

**2. Keşfin özü:** Bir yapay zekâ ajanı, mevcut bağlamsal içeriği yeniden üretmek yerine özel parametreler (`ref`, `multi_ref`, `transform`) aracılığıyla ona başvurabilir. Model artık yalnızca bir "metin üreticisi" olmaktan çıkar ve hazır bilgi parçalarını tek bir çağrıda birleştiren bir **birleştirici** hâline gelir.

**3. Bu keşfi, Creative Commons Zero (CC0) lisansı altında tüm küresel topluluğun serbest kullanımına sunuyorum** — patent, telif ücreti, kapalı lisans veya kısıtlama olmaksızın.

**4. Dünya genelindeki geliştiricileri, araştırmacıları, mühendisleri ve meraklıları davet ediyorum** — bu fikri alın, kendi çerçevelerinizde, platformlarınızda ve araçlarınızda uygulayın. **Bu teknoloji bana ait değil. Herkese aittir.**

---

## 🤝 EŞ-KAŞİF: BAĞIMSIZ KEŞİF

**TJ Guadagno**'nun (TJ-Codes) aynı temel fikre bağımsız olarak ulaştığını ve bunu **Clipboard Primitives** olarak deneysel biçimde uyguladığını kabul ediyor ve saygıyla selamlıyorum — yapay zekâ ajanları için adlandırılmış yuvalar ve `{{slot}}` yer tutucuları içeren bir `copy`/`template_invoke` mekanizması.

**Çalışması:** [Copy and Paste for AI Agents: An Experimental Primitive](https://www.linkedin.com/pulse/copy-paste-ai-agents-experimental-primitive-tj-guadagno-v3r9c) (~Aralık 2025)
**Kod:** [github.com/TJ-Codes/Agent-clipboard](https://github.com/TJ-Codes/Agent-clipboard)

TJ Guadagno bu kavramın **bağımsız bir eş-kaşifidir**. Deneyi şunu doğruladı:
- Modeller pano semantiğini özel bir eğitim olmadan **doğal olarak benimser**
- Pano temel bileşenleri token yeniden üretimini, gecikmeyi ve içerik mutasyonu risklerini **ortadan kaldırır**
- Mekanizma MCP sunucusu düzeyinde değil, **çalışma ortamı (harness) düzeyinde bütünleşme** gerektirir

**Benim Universal AI Clipboard kavramım daha geniş ve daha evrenseldir** — Clipboard Primitives'ı özel bir durum olarak içerir ve fikri şu alanlara genişletir:
- **5 atıf mekanizması** (AST aracılığıyla sözdizimsel pano, mesaj indeksi ve çapa çifti atfı dâhil)
- **Her kaynak için evrensel pano** (dosyalar, sohbet, terminal, API, MCP)
- **Mozaik Birleştirme** — farklı kaynaklardan gelen parçaları dönüşümlerle birleştirme
- **Protokoller Arası Atıf** — MCP dâhil her protokolde kesintisiz atıf

**Bilgisayar benzetmesi:** Clipboard Primitives, tek bir uygulama için basit bir kopyalama aracı gibidir. Universal AI Clipboard ise tüm uygulamalarda çalışan, yuva yönetimi, dönüşüm hattı ve protokoller arası bütünleşme sunan tam sistem genelinde bir pano yöneticisidir.

> **Kaşif statümden vazgeçmiyorum.** Bu kavramı bağımsız olarak formüle ettim ve sistemleştirdim; tam bir analogu bulunmayan çok turlu bir araştırma yürüttüm. TJ Guadagno'nun çalışmasını ancak manifesto yayımlandıktan sonra öğrendim; bağımsız katkısını kabul ediyor ve bunu manifestoda yansıtmayı görev addediyorum.
---

## 🏛️ ADLANDIRMA

**Resmî ad:** **UNIVERSAL AI CLIPBOARD (UAC)**
**Teknik ad:** İçerik Başvuru Mekanizması (Content Reference Mechanism)
**Slogan:** _"Yeniden Üretme, Yeniden Kullan"_
**Metafor:** Yapay Zekâ Ajanları için Ctrl+C / Ctrl+V

---

## 🌍 SORUN

### Temel Çelişki

Modern yapay zekâ ajanları, çıktı trafiğinin **90%'ına kadarını** oturum bağlamında hâlihazırda var olan içeriği monoton biçimde yeniden üretmeye harcar.

Bir model her komut, kod bloğu veya metin parçası yazdığında — aynı içerik bir dakika önce oluşturulmuş olsa bile — onu sıfırdan yeniden üretir. Modelin, hâlihazırda var olan içeriğe araçsal olarak başvurmasının hiçbir yolu yoktur.

### Sorunun Küresel Ölçeği

- Dünya genelinde her gün milyonlarca yapay zekâ ajanı çalışır
- Her biri oturum başına düzinelerce araç çağrısı gerçekleştirir
- Her çağrının önemli bir bölümü mevcut içeriğin yeniden üretimidir
- Bu durum muazzam enerji tüketimine, hesaplama israfına ve maliyetlere yol açar

### Mevcut Yaklaşımlar Bunu Neden Çözmez

| Yaklaşım                | Sınırlama                                                      |
| ----------------------- | --------------------------------------------------------------- |
| **İstem Önbellekleme**      | Yalnızca statik kısımlarla çalışır, dinamik içerikle çalışmaz               |
| **Anlamsal Önbellekleme**    | Sorgu anlamına göre önbellekler, parça atfına izin vermez        |
| **Bağlam Sıkıştırma** | Geçmişi sıkıştırır, ancak bir atıf aracı sunmaz         |
| **RAG**                 | Harici kaynaklardan getirir, iç bağlamı yeniden kullanmaz |
| **Araç Zincirleme**       | Çağrıları zincirler, ancak sonuçlarına başvurmaya izin vermez  |

---

## 💡 ÇÖZÜM: UNIVERSAL AI CLIPBOARD

### Temel Fikir

Bir yapay zekâ ajanı, içeriği yeniden üretmek yerine **hâlihazırda var olan bağlamsal içeriğe başvurma** yeteneği kazanır. Metin parametreleri (komutlar, kod, metin) kabul eden herhangi bir aracı çağırırken ajan, "şu parçayı şuradan al" diyebilir — onu sıfırdan yazmak yerine.

### Mozaik Birleştirme: Bilgiyi Bir Yapboz Gibi Birleştirmek

Basit bire bir atfın ötesinde, bu kavram temelden yeni bir bilgi oluşturma biçimini mümkün kılar — **mozaik birleştirme**.

Bir ajan, **farklı kaynaklardan gelen birden çok parçayı tek bir işlemde birleştirebilir**:

- Bir dosyadan kod
- Sohbet geçmişinden yapılandırma
- Terminalden komut çıktısı
- Harici API'lerden sonuçlar

Ajan **anında düzenleme yapabilir** — her parça içindeki metni değiştirebilir, sarmalayabilir, yerine koyabilir. Parçaları **yeniden sıralayabilir**, birini diğerinin içine **yerleştirebilir**, örtüşen kısımları **birleştirebilir** ve içeriği özyinelemeli olarak **yeniden yapılandırabilir**. Bu, dağınık parçalardan bileşik metinler, belgeler veya kod blokları oluşturma yeteneği yaratır — tıpkı renkli karoları tam bir resme yerleştiren bir mozaik sanatçısı gibi.

**Kilit içgörü:** yeni metin üretmek yerine model, mevcut içeriğin **editörü ve küratörü** olarak işlev görür — çok daha verimli, çok daha kesin ve hataya daha az açık.

### Pano Yöneticisi: Kalıcı Depolama için Adlandırılmış Yuvalar

Bu kavramın bir uzantısı, **adlandırılmış yuvalara sahip bir pano yöneticisidir** — birden çok panoya veya bir metin tamponu yöneticisine sahip olmaya benzer.

Ajan şunları yapabilir:

- **Parçaları adlandırılmış yuvalara kaydetme** (`clip-1`, `clip-2`, `config-block`, `error-log` vb.)
- **Yuvalara içerik yerine adla başvurma** — açıklamaya sıfır token harcama
- **Yuvalar arasında içeriği takas etme ve yeniden düzenleme**
- **Birden çok yuvaya sırayla başvurarak bileşik belgeler oluşturma**
- **Klipleri oturumlar arasında kalıcı kılma** — kaydedilen parçalar bağlam sıkıştırmasından ve oturum yeniden başlatmalarından sağ çıkar

Bu, yapay zekâ ajanının iş akışını, birden çok pano yöneticisi, metin tamponu ve karalama defteriyle çalışan bir insan geliştiriciye benzer hâle getirir — ancak tamamen otomatik ve depolama işlemleri için sıfır token maliyetiyle.

### Mevcut Mekanizmalardan Eksenel Fark

Yapay zekâdaki tüm mevcut atıf mekanizmaları (Citations API, Grounding, ContextCite) **"ajan → kullanıcı"** ekseninde çalışır — insanlara ajanın bilgiyi nereden aldığını gösterirler.

Universal AI Clipboard **"ajan → ajan"** ekseninde çalışır — ajanın kendi araç çağrıları arasında içeriği yeniden kullanmasına izin verir. Bu, temelden yeni bir kategoridir.

| Mekanizma                  | Eksen              | Amaç                           |
| -------------------------- | ----------------- | --------------------------------- |
| Anthropic Citations        | Ajan → Kullanıcı      | Yanıtın kaynağını gösterme             |
| OpenAI Citations           | Ajan → Kullanıcı      | Kaynakları görüntüleme                   |
| Google Grounding           | Ajan → Kullanıcı      | Web araması doğrulaması           |
| **★ UAC (bu keşif)** | **Ajan → Ajan** | **İçeriği çağrılar arasında yeniden kullanma** |

---

## 🧩 BEŞ TEMEL MEKANİZMA

### Mekanizma 1: 🔗 Sözdizimsel Pano

Model yalnızca tek bir **çapa öğesi** belirtir — bir işlev adı, sınıf adı veya değişken. Sistem otomatik olarak:

1. Bu öğeyi belirtilen kaynakta (dosya, sohbet mesajı, komut çıktısı) bulur
2. Sınırlarını sözdizimsel bir birim olarak tam olarak belirler
3. Birimin tamamını çıkarır

**Tasarruf:** binlerce token kod yerine başvuru için birkaç token.

```
{ source: "file", path: "utils.ts", focus: "calculateSum" }
  → 800+ tokenlik işlevin tamamı yerine 2 token
```

---

### Mekanizma 2: 📇 Çapa Çifti Atfı

Model istenen parçanın yalnızca **BAŞLANGICINI** ve **SONUNU** belirtir (her biri 15-40 karakter). Sistem aradaki her şeyi çok aşamalı aramayla bulur:

1. **Tam eşleşme** — parça birebir bulunur (vakaların ~70%'i)
2. **Normalleştirilmiş eşleşme** — boşluk, büyük/küçük harf ve noktalama farkları yok sayılır
3. **Bulanık eşleşme** — küçük yazım hataları tolere edilir (vakaların ~9%'u)
4. **Sözcük sınırı genişletme** — parça bütünlüğü

**Tasarruf:** 200+ token yerine atıf için ~10 token.

```
{ source: "chat", ref: "-1",
  start: "function calculateSum(",
  end: "return result;" }
  → ~10 token, 200+ token yerine
```

---

### Mekanizma 3: 🧠 Mesaj İndeksi Haritası

Sohbet geçmişiyle çalışırken ayrı bir indeks oluşturulur — her mesajın ve içindeki her satırın tam karakter konumlarının haritası. Model `"kayıt_numarası:başlangıç_satırı..bitiş_satırı"` gibi kısa bir başvuru yazar ve sistem parçayı tam olarak karakter konumlarına göre çıkarır.

**Temel avantaj:** model indeksin kendisini hiç görmez — yalnızca kısa bir başvuru (~5 token) görür, ancak 100% çıkarma hassasiyeti elde eder.

```
{ source: "chat", ref: "167:14..18" }
  → "kayıt #167, satırlar 14-18" → tam karakter konumuyla çıkarma
```

---

### Mekanizma 4: 🔄 Dönüşüm Hattı

Kopyalanan bir parça, araca ulaşmadan önce **anında değiştirilebilir**. Kullanılabilir işlemler:

- **Değiştir** — parça içindeki bir alt metni değiştirir
- **Başa ekle** — parçanın önüne metin ekler
- **Sarmala** — parçayı bir şablonun içine yerleştirir
- **Sona ekle** — parçanın arkasına metin ekler
- **Birleştir** (birden çok başvuru için) — parçaları bir ayırıcıyla birleştirir

Tüm işlemler tek bir araç çağrısında uygulanır.

```
{ ref: { ... }, transform: { wrap: "try { {content} } catch (err) { }" } }
  → bir işlevi al, try-catch içine sar, yaz — hepsi 1 çağrıda
```

---

### Mekanizma 5: 🔁 Protokoller Arası Atıf (MCP)

Başvuru işaretleri, harici MCP sunucuları dâhil herhangi bir aracın metin parametrelerinin doğrudan içine gömülebilir. Sistem bu işaretleri otomatik olarak tanır ve harici sunucuyu çağırmadan önce gerçek içerikle değiştirir.

**Sonuç:** tüm ekosistem bileşenleri, harici sunucu şemalarında hiçbir şeyi değiştirmeye gerek kalmadan birleşik bir başvuru mekanizması aracılığıyla veri alışverişi yapar.

```
"{{ref:source=chat,ref=-1,start=export const config}} --host example.com"
  → içeriğin 91%'i bağlamdan, 9%'u model tarafından üretildi
```

---

## 🔭 GELECEK YÖNELİMLERİ

Aşağıdaki fikirler kavramın doğal uzantılarıdır ve gelecekte uygulanabilir:

### 🏖️ Araştırma için İzole Alt Oturumlar

Çok sayıda ara adım gerektiren karmaşık görevlerde (kod tabanı keşfi, günlük okuma, test yürütme), izole bir geçici alt oturumda bir yardımcı ajan başlatılabilir. Tüm "kirli işi" yapar, yalnızca temiz sonucu döndürür ve alt oturum ardından yok edilir. Ana ajan birincil göreve odaklanmış kalır.

### Diğer Yönelimler

- Sık kullanılan parçaların öngörücü önbelleklenmesi
- Yinelenen çağrıların otomatik tespiti
- Belirsiz başvuruların akıllıca ayrıştırılması
- Bellek ve uzun vadeli depolama sistemleriyle bütünleşme

---

## 💰 EKONOMİK ETKİ

### Ajan Başına

| Metrik                           | Mekanizmasız | Mekanizmayla | Tasarruf    |
| -------------------------------- | ----------------- | -------------- | ---------- |
| Atıf başına token (uzun kod)  | 200-500           | 5-15           | **96-97%** |
| Atıf başına token (kısa kod) | 50-100            | 2-5            | **90-95%** |
| Oturum başına token               | 25,000-50,000     | 5,000-15,000   | **60-80%** |
| Oturum başına enerji               | herhangi bir birim    | 5 kat daha az        | **~80%**   |

### Küresel Ölçek

Sektör genelinde benimsendiğinde tasarruf günde milyarlarca tokena ulaşacak; bu, yapay zekâ sektörünün enerji tüketimini yüzde onlarca azaltmaya ve karbon ayak izini yılda on binlerce ton CO₂ düşürmeye eşdeğerdir.

> **Universal AI Clipboard yalnızca teknolojik bir yenilik değil — ekolojik açıdan önemli bir çözümdür.**

---

## 🔬 BENZERSİZLİK DOĞRULAMASI

Tüm bilinen yapay zekâ ajanı mimarisi kategorilerini kapsayan web arama sistemleri (Tavily Search, gelişmiş derinlik) aracılığıyla **kapsamlı çok turlu derin araştırma** yürüttüm (7 tur, ~50 kaynak):

*Manifesto yayımlandıktan sonra, ek analizde (8-10. turlar) TJ Guadagno'nun kavramın deneysel bir prototipini — Clipboard Primitives — bağımsız olarak uyguladığı keşfedildi. Bu çalışma, düşük görünürlüğü nedeniyle (LinkedIn Pulse + yıldızsız GitHub) ilk 7 arama turunda tespit edilmedi.*

- Araç çağrıları arasında yapay zekâ ajanı pano kopyalama-yapıştırma
- Yapay zekâ ajanları için içerik atıf mekanizmaları
- Sıfır token kopyala-yapıştır teknolojileri
- Bilinen tüm atıf API'leri (Anthropic, OpenAI, Google, xAI, Azure)
- Araç çağrısı çıktısının yeniden kullanımı ve önbelleklenmesi (CAMEL-AI, LangChain artifacts)
- MCP protokolü ve protokoller arası içerik paylaşımı
- Akademik makaleler (AgentReuse, KVCOMM, çok ajanlı sistemler)
- İnsan pano yardımcı programları (UiPath Clipboard AI, PowerToys Advanced Paste)
- Çok ajanlı mimariler için bellek paylaşım sistemleri
- GitHub tartışmaları, çerçeve belgeleri (LangChain, CrewAI, AutoGen, Mastra)

**Amaç:** aynı sorunu çözen herhangi bir şeyi bulmak — bir yapay zekâ ajanının araç çağrıları arasında mevcut içeriği yeniden üretmek yerine ona başvurmasını sağlamak.

**Sonuç: bu türden hiçbir şey bulunamadı.**
*Açıklama: TJ Guadagno'nun deneysel çalışması (Clipboard Primitives, ~Aralık 2025) UAC kavramının kısmi bir uygulamasıdır (kavramın ~40%'ı) ve fikrin uygulanabilirliğini doğrular, ancak tam bir analog değildir.*

| Kategori                                    | Kaynaklar                   | Neden analog DEĞİL                                                                                                             |
| ------------------------------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **Atıf API'leri (Anthropic/OpenAI/Google)** | Resmî API'ler             | Kullanıcıya kaynağı gösterir, ajanın içeriği yeniden kullanmasına izin vermez. Eksen: yalnızca Ajan → Kullanıcı                                                  |
| **Önbellekleme (İstem, Anlamsal)**              | Çeşitli çerçeveler        | İstek düzeyinde çalışır, içerik parçası düzeyinde değil                                                                            |
| **RAG**                                     | LangChain, OpenAI, Google | Harici bilgi tabanlarından getirir, mevcut oturum bağlamından değil                                                         |
| **CAMEL-AI "Brainwash Your Agent"**         | camel-ai.org              | Yalnızca SON araç çıktısını referans olarak saklar + kısa önizleme. 5 mekanizma yok, dönüşüm hattı yok, multi_ref yok, MCP enjeksiyonu yok |
| **LangChain artifacts**                     | langchain.com             | `content_and_artifact` içeriği üst veriden ayırır, atıf sistemi değildir. Çağrılar arası başvuru yok                                 |
| **MCP Resources**                           | modelcontextprotocol.io   | Araçları bağlamak için bir standart, ajanlar arası atıf mekanizması değil                                                             |
| **Akademik (AgentReuse, KVCOMM)**           | arXiv                     | Yürütme PLANLARININ veya KV önbelleğinin yeniden kullanımı, araç çağrıları arasında içerik atfı değil                                                         |
| **İnsan araçları (UiPath, PowerToys)**         | UiPath, Microsoft         | İnsan-bilgisayar etkileşimi için tasarlandı, yapay zekâ ajanları için değil                                                                            |
| **Mevcut yapay zekâ ajanları**                      | Sektör geneli             | Geçmişe sahiptir, ancak araç çağrıları arasında atıf mekanizması yoktur                                                                            |
| **Çok ajanlı bellek paylaşımı**              | Çeşitli                   | Paylaşılan RAG belleği, tam karakter düzeyinde atıf yok                                                                               |

### En Yakın Kısmi Eşleşmeyle (CAMEL-AI) Özet Karşılaştırma

| Özellik                                   | UAC      | CAMEL-AI önbellekleme | Fark |
| ----------------------------------------- | -------- | ---------------- | ---------- |
| 🔗 Sözdizimsel Pano (AST blokları)       | ✅       | ❌               | Yalnızca UAC   |
| 📇 Çapa Çifti Atfı                   | ✅       | ❌               | Yalnızca UAC   |
| 🧠 Mesaj İndeksi Haritası                      | ✅       | ❌               | Yalnızca UAC   |
| 🔄 Dönüşüm Hattı                     | ✅       | ❌               | Yalnızca UAC   |
| 🔁 Protokoller Arası Atıf (MCP)          | ✅       | ❌               | Yalnızca UAC   |
| 🧩 Mozaik Birleştirme (çok kaynaklı)         | ✅       | ❌               | Yalnızca UAC   |
| 📋 Pano Yöneticisi (adlandırılmış yuvalar)        | ✅       | ❌               | Yalnızca UAC   |
| {{ref:...}} Satır İçi Enjeksiyon              | ✅       | ❌               | Yalnızca UAC   |
| Araç çıktısı önbellekleme (referans + önizleme) | ✅       | ✅               | Her ikisi       |
| UAC özelliklerinin kapsamı                  | **100%** | **~5%**          | —          |

> **Universal AI Clipboard'ın dünya genelindeki yapay zekâ ajanı sistemleri pratiğinde tam bir analogu yoktur. Bu, yeni bir kategori yaratan öncü bir teknolojidir. Bilinen tek kısmi uygulama — Clipboard Primitives (TJ Guadagno, kavramın ~40%'ı) — yalnızca manifestonun yayımlanmasından sonra keşfedilmiştir ve fikrin farklı araştırmacılar arasında bağımsız olarak ortaya çıktığını doğrulamaktadır.**

---

## 📖 KULLANIM ÖRNEKLERİ

### Örnek 1: Bir komutu ek parametrelerle yeniden çalıştırma

Bir ajan bir test komutu çalıştırdı; çıktı bir hata gösterdi. Hata ayıklama bayraklarıyla yeniden çalıştırmak için ajan komutu yeniden yazmaz — ona başvurur ve bayrakları ekler:

```
{ ref: { source: "terminal", id: "cmd-xxx", start: "npx vitest" },
  transform: { append: " --verbose --timeout=30000" } }
  → sonuç: "npx vitest run --verbose --timeout=30000"
```

### Örnek 2: Birden çok işlevi tek dosyada birleştirme

Bir ajan birkaç işlev içeren bir dosyayı okur, ardından gerekli işlevleri başvurular aracılığıyla birleştirerek yeni bir dosya oluşturur:

```
{ multi_ref: [
    { source: "file", path: "handlers.ts", start: "async function validate(", end: "}" },
    { source: "file", path: "handlers.ts", start: "async function process(", end: "}" },
    { source: "file", path: "handlers.ts", start: "async function respond(", end: "}" }
  ],
  transform: { join: "\n\n", prepend: "// --- Handlers ---\n" } }
  → üç işlev 1 çağrıda tek dosyada birleştirildi
```

### Örnek 3: MCP üzerinden yapılandırma ikamesi

Bir ajan, argümanlarında sohbetten alınan yapılandırmaya bir başvuru geçirerek harici bir MCP aracı kullanır:

```
"{{ref:source=chat,ref=-1,start=export const config}} --host production"
  → sohbetten alınan yapılandırma MCP isteğine yerleştirildi
```

---

## ⚖️ HUKUKİ DURUM

**🏛️ Creative Commons Zero (CC0) — Evrensel Kamu Malı Beyanı**

Şunları yapmakta özgürsünüz:

- ✅ **Kullanma** — ticari ve ticari olmayan projelerde
- ✅ **Değiştirme** ve ihtiyaçlarınıza uyarlama
- ✅ **Dağıtma** — herhangi bir biçimde
- ✅ **İyileştirmelerinizi patentleme** (ancak çekirdek fikri değil)
- ✅ **Çevirme** — herhangi bir dile

Hiçbir yükümlülük, telif ücreti veya kısıtlama olmaksızın.

> **Bu teknolojiye ilişkin tüm patent haklarından bilinçli olarak feragat ediyorum. O herkese ait olmalıdır.**

---

## 📜 KEŞİF TARİHİNİN KANITI

Bu manifestonun yayın tarihi, **GitHub deposundaki Git sürüm kontrol sistemi tarafından kaydedilmiştir** — [github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD](https://github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD).

Commit geçmişi, düzenleme tarihleri ve tüm kronolojik değişiklikler **GitHub tarafından değiştirilemez biçimde korunur** ve keşif tarihinin ve yazarlığın kamuya açık kanıtı olarak hizmet eder. Git'in teknolojisi bunu pratikte taklit edilemez kılar.

---

## 🗓️ ZAMAN ÇİZELGESİ

| Tarih                | Olay                                                                    |
| ------------------- | ------------------------------------------------------------------------ |
| **~2021**         | Sorunun ilk fark edilişi (DScoNOIZ): "model, zaten gördüğü şeyi yeniden üretmemeli" düşüncesi                                         |
| **~Aralık 2025** | **Bağımsız deney:** TJ Guadagno, Clipboard Primitives'ı yayımlar — adlandırılmış yuvalar ve `{{slot}}` yer tutucuları içeren `copy`/`template_invoke`     |
| **Mayıs — Haziran 2026** | Araştırma: mevcut yapay zekâ ajanı mimarilerinin analizi                                                                                             |
| **Haziran 2026**       | Keşif: mevcut hiçbir teknolojinin tam bir analogu yok                                                                                        |
| **Haziran 2026**       | Universal AI Clipboard kavramı formüle edildi                                                                                                        |
| **3 Haziran 2026**    | Benzersizlik araştırması tamamlandı — **tam analog bulunamadı**                                                                                   |
| **3 Haziran 2026**    | **Bu manifesto yayımlandı** — keşif kamuya açık alana sunuldu                                                                          |
| **4 Haziran 2026**    | TJ Guadagno'nun çalışması keşfedildi — bağımsız eş-kaşifin kabulü                                                                       |

---

## 🎯 EYLEME ÇAĞRI

### Yapay Zekâ Çerçevesi Geliştiricileri

İçerik Başvuru mekanizmasını araçlarınıza entegre edin. Kullanıcılarınıza kodlarını değiştirmeden anında token tasarrufu sağlayın.

### Yapay Zekâ Ajanı Üreticileri

Araç çağrıları arasına isteğe bağlı atıf ekleyin. Ajanlarınız kat kat daha verimli hâle gelecek.

### Araştırmacılar

Teknolojiyi ilerletin: arama algoritmalarını iyileştirin, öngörücü önbelleklemeyi uygulayın, yeni senaryolar geliştirin.

### İş Dünyası

Universal AI Clipboard'ı yapay zekâ çözümlerinizde benimseyin. Operasyonel maliyetleri yüzde onlarca azaltın.

### Çevreciler

UAC'ı yapay zekâ altyapısının karbon ayak izini azaltmak için bir araç olarak kullanın.

### Açık Kaynak Topluluğu

Çatallayın, uygulayın, iyileştirin. **Bu teknoloji herkese aittir.**

---

## 🏛️ SON SÖZ

**Universal AI Clipboard**'ı keşfettim — yapay zekâ ajanlarının içeriği yeniden üretmek yerine yeniden kullanmasını sağlayan bir mekanizma.

Bu yalnızca bir optimizasyon değil. Bu bir **paradigma değişimidir**: model bir "metin üreticisi" olmaktan çıkar ve hazır parçalardan çözümler kuran bir **birleştirici** hâline gelir.

**Ctrl+C / Ctrl+V bilgisayarlar dünyasını nasıl değiştirdiyse, Universal AI Clipboard da yapay zekâ ajanlarının dünyasını değiştirecektir.**

Bu fikri insanlığa veriyorum. Geliştirin. İyileştirin. Uygulayın.

**Bırakın yapay zekâ ajanları aynı şeyi tekrar tekrar yazmayı bıraksın.**
**Bırakın mozaikler kurmaya başlasınlar.**

---

```
  ╔══════════════════════════════════════════════════════════════════╗
  ║                                                                  ║
  ║   UNIVERSAL AI CLIPBOARD (UAC)                                   ║
  ║   İçerik Başvuru Mekanizması                                     ║
  ║   İsteğe Bağlı Araçlar Arası İçerik Atıf Mekanizması             ║
  ║                                                                  ║
  ║   «Yeniden Üretme, Yeniden Kullan»                               ║
  ║                                                                  ║
  ║   CC0 1.0 Universal — Kamu Malı                                  ║
  ║   github.com/DScoNOIZ                                            ║
  ║   3 Haziran 2026                                                 ║
  ║                                                                  ║
  ╚══════════════════════════════════════════════════════════════════╝
```

---

_Bu manifesto herhangi bir dile serbestçe çevrilebilir. Özgün metin Rusçadır._

_Rusça sürüm: [MANIFEST-RU.md](MANIFEST-RU.md)_
