# Finansal Portföy Risk Analizi

**Kısa Açıklama**
Bu proje, çok varlıklı bir yatırım portföyünün risk profilini nicel olarak analiz eder. Projede veri çekme, temizleme, EDA (keşifsel veri analizi), portföy oluşturma, risk ölçümleri (volatilite, VaR, CVaR, Sharpe, max drawdown vb.), backtest, stres testi ve basit bir Streamlit demo yer alır.

---

## Ana Bulgular (Örnek Başlıklar — proje ilerledikçe doldur)

* Equal-weight portföy yıllık volatilite: **X%**
* 95% günlük VaR: **Y%**
* Backtest sonucu: CAGR = **Z%**, Max Drawdown = **W%**

---

## İçindekiler

* [Gereksinimler](#gereksinimler)
* [Kurulum & Çalıştırma](#kurulum--çalıştırma)
* [Veri Kaynakları](#veri-kaynakları)
* [Proje Yapısı](#proje-yapısı)
* [Ana Fonksiyonlar](#ana-fonksiyonlar)
* [Nasıl çalışır? (Adımlar)](#nasıl-çalışır-adımlar)
* [Sonuçların Sunumu](#sonuçların-sunumu)
* [Lisansa ve İletişim](#lisans-ve-iletişim)

---

## Gereksinimler

* Python 3.9+
* Önerilen paketler (requirements.txt içinde):

  * pandas, numpy, scipy
  * matplotlib, seaborn, plotly
  * yfinance
  * scikit-learn
  * statsmodels, arch (opsiyonel)
  * streamlit

## Kurulum & Çalıştırma

1. Repo'yu klonla: `git clone <repo-url>`
2. Sanal ortam oluştur:

   ```bash
   python -m venv venv
   source venv/bin/activate  # mac/linux
   venv\Scripts\activate     # windows
   ```
3. Paketleri yükle:

   ```bash
   pip install -r requirements.txt
   ```
4. JupyterLab ile notebookları aç:

   ```bash
   jupyter lab
   ```
5. Streamlit demo çalıştır (opsiyonel):

   ```bash
   streamlit run app/streamlit_app.py
   ```

---

## Veri Kaynakları

* Hisse fiyatları: yfinance (`Adj Close`), örnek tarih aralığı: `2019-01-01` — `2024-12-31`.
* Benchmark: SPY (S&P 500 ETF).
* Opsiyonel: VIX (CBOE), Dünya Bankası / FRED verileri.

---

## Proje Yapısı (Örnek)

```
/data
/notebooks
  - 01_data_download.ipynb
  - 02_eda.ipynb
  - 03_portfolio_metrics.ipynb
  - 04_backtest_and_stress.ipynb
/app
  - streamlit_app.py
/utils
  - data_utils.py
  - portfolio_utils.py
requirements.txt
README.md
```

---

## Ana Fonksiyonlar (özet)

* `download_data(symbols, start, end)` — yfinance ile fiyatları çeker.
* `compute_returns(prices, method='simple')` — günlük getirileri hesaplar.
* `annualize_return(returns)` / `annualize_vol(returns)` — yıllıklandırma.
* `portfolio_performance(weights, returns)` — CAGR, vol, Sharpe, max drawdown.
* `optimize_mean_variance(returns)` — efficient frontier.
* `historical_var(returns, alpha=0.05)` / `cvar(returns, alpha)` — risk ölçümleri.
* `backtest_portfolio(weights_series, prices, rebalance)` — zaman içi simülasyon.
* `risk_contribution(weights, cov_matrix)` — her varlığın riske katkısı.

---

## Nasıl çalışır? (Adımlar)

1. Veri çek (yfinance) ve `Adj Close` ile fiyat serilerini hazırla.
2. Getirileri hesapla (günlük simple returns veya log returns).
3. EDA: özet istatistikler, korelasyon, rolling vol gibi görseller.
4. Portföy tanımla: equal-weight, mean-variance optimization, min-vol vb.
5. Risk metriklerini hesapla: volatilite, Sharpe, VaR, CVaR, max drawdown.
6. Backtest ve rebalance simülasyonu yap.
7. Stres testi, worst-day analizi, Monte Carlo (opsiyonel).
8. Sonuçları raporla ve Streamlit ile küçük demo oluştur.

---

## Sonuçların Sunumu

* Notebook başına bir "Executive Summary" hücresi ekle (kısa bulgular).
* README içinde kısa bir "Ana Bulgular" bölümü bulunsun.
* Streamlit demo ile interaktif ağırlık değişimi ve metrikleri göster.
* 1–2 dk'lık kısa video/gif ekle (opsiyonel ama çok etkili).

---

## Lisans ve İletişim

* Lisans: MIT (isteğe bağlı)
* İletişim: İsim / LinkedIn / E-posta (doldur)

---

# GitHub Issues (Önerilen issue'lar — doğrudan kopyala-yapıştır ile GitHub'a ekleyebilirsin)

Aşağıdaki başlıklar `Issues` olarak açılabilir. Her issue kısa açıklama, kabul kriterleri ve etiket önerisi içerir.

---

### Issue 1 — Project setup & environment

**Açıklama:** Repo oluştur, `requirements.txt` ekle, sanal ortam talimatlarını README’ye yaz.
**Kabul Kriterleri:** `requirements.txt` var, README içinde kurulum bölümü hazır.
**Etiketler:** `setup`, `documentation`

---

### Issue 2 — Data download utility

**Açıklama:** `download_data(symbols, start, end)` fonksiyonunu yaz. Eksik veri kontrolü ve logging ekle.
**Kabul Kriterleri:** Fonksiyon örnek semboller ile test edildi ve `data/` dizinine kaydetti.
**Etiketler:** `backend`, `data`

---

### Issue 3 — Compute returns & basic EDA

**Açıklama:** `compute_returns` fonksiyonu, günlük ve aylık dönüşümler; EDA notebook (özet istatistikler, görseller).
**Kabul Kriterleri:** EDA notebook'unda fiyat grafikleri, korelasyon heatmap ve rolling vol bulunuyor.
**Etiketler:** `notebook`, `eda`

---

### Issue 4 — Portfolio metrics functions

**Açıklama:** `annualize_return`, `annualize_vol`, `portfolio_performance` (CAGR, Sharpe, max drawdown).
**Kabul Kriterleri:** Fonksiyonlar testlerle doğrulandı ve örnek çıktı notebook'ta gösterildi.
**Etiketler:** `backend`, `math`

---

### Issue 5 — Mean-variance optimizer & efficient frontier

**Açıklama:** Markowitz optimizasyonu fonksiyonu, efficient frontier çizimi.
**Kabul Kriterleri:** Frontier çizildi; örnek en düşük vol ve en yüksek Sharpe portföyleri bulundu.
**Etiketler:** `ml`, `optimization`

---

### Issue 6 — VaR & CVaR calculations

**Açıklama:** Historical VaR, parametric VaR, CVaR fonksiyonlarını ekle.
**Kabul Kriterleri:** 95% ve 99% VaR hesapları notebook'ta gösterildi.
**Etiketler:** `risk`, `math`

---

### Issue 7 — Backtesting engine & rebalance

**Açıklama:** Basit backtest fonksiyonu yaz—rebalance frekansını (monthly, quarterly) desteklesin.
**Kabul Kriterleri:** Backtest sonuçları (equity curve), benchmark karşılaştırması ve temel metrikler hesaplandı.
**Etiketler:** `backtest`, `simulation`

---

### Issue 8 — Stress testing & Monte Carlo

**Açıklama:** Worst-N-days analizi, Monte Carlo simülasyonu (basit) ve stres senaryoları.
**Kabul Kriterleri:** Stres test raporu ve birkaç görsel sunuldu.
**Etiketler:** `risk`, `simulation`

---

### Issue 9 — Risk attribution & contribution

**Açıklama:** `risk_contribution` fonksiyonu ile varlık bazlı katkı hesabı ve görselleştirme.
**Kabul Kriterleri:** Her varlığın portföy volatilitesine katkısı hesaplandı ve grafikle gösterildi.
**Etiketler:** `risk`, `visualization`

---

### Issue 10 — Streamlit demo app

**Açıklama:** Minimal Streamlit uygulaması: kullanıcı ağırlıkları slider ile değiştirir; metrikler anlık hesaplanır.
**Kabul Kriterleri:** `app/streamlit_app.py` çalışıyor ve lokalden test edildi.
**Etiketler:** `ui`, `demo`

---

### Issue 11 — Documentation & README finalization

**Açıklama:** README son hâlini hazırla, örnek görseller ekle ve repo kökünü temizle.
**Kabul Kriterleri:** README tamam, ana bulgular eklendi ve repo düzenlendi.
**Etiketler:** `documentation`

---

### Issue 12 — Optional: Unit tests & CI

**Açıklama:** Temel fonksiyonlar için pytest testleri yaz ve GitHub Actions ile CI ekle.
**Kabul Kriterleri:** En az 5 test; basit workflow dosyası eklendi.
**Etiketler:** `tests`, `ci`

---

## Notlar

* İstersen bu issue metinlerini doğrudan GitHub Issues API veya GitHub web arayüzüne ekleyebilecek hazır JSON/başlık formatı da oluşturabilirim.
* Her issue için tahmini süre istersen haftalık tahminler de ekleyebilirim.

---

*Hazır olduğunda istersen bu markdown'u doğrudan repo'na eklemene yardımcı olurum veya her issue'yu tek tek GitHub'a yazacak formatta (title/body/labels) dışa aktarırım.*
