# 👻 Ghost Turvaturvamoduuli
**PowerShell-pohjainen Windows & Azure Turvallisuuden Kovettaminen**

> **Ennakoiva turvallisuuden kovettaminen Windows-päätteille ja Azure-ympäristöille.** Ghost tarjoaa PowerShell-pohjaisia kovettamisfunktioita, jotka voivat auttaa vähentämään yleisiä hyökkäysvektoreita poistamalla tarpeettomia palveluja ja protokollia käytöstä.

## ⚠️ Tärkeät Vastuuvapauslausekkeet

**TESTAUS VAADITAAN**: Testaa Ghost aina ensin ei-tuotantoympäristöissä. Palvelujen poistaminen käytöstä voi vaikuttaa laillisiin liiketoimintafunktioihin.

**EI TAKUITA**: Vaikka Ghost kohdistaa yleisiä hyökkäysvektoreita, mikään turvallisuustyökalu ei voi estää kaikkia hyökkäyksiä. Tämä on yksi osa kattavaa turvallisuusstrategiaa.

**TOIMINNALLINEN VAIKUTUS**: Jotkin funktiot voivat vaikuttaa järjestelmän toimivuuteen. Tarkista jokainen asetus huolellisesti ennen käyttöönottoa.

**AMMATTIMAINEN ARVIOINTI**: Tuotantoympäristöjen osalta, konsultoi turvallisuusammattilaisia varmistaaksesi, että asetukset vastaavat organisaatiosi tarpeita.

## 📊 Turvallisuusmaisema

Kiristysohjelmahaitat saavuttivat **57 miljardia dollaria vuonna 2025**, ja tutkimus osoittaa, että monet onnistuneet hyökkäykset hyödyntävät Windows-peruspalveluja ja virheellisiä konfiguraatioita. Yleisiä hyökkäysvektoreita ovat:

- **90% kiristysohjelmatapauksista** sisältää RDP-hyväksikäyttöä
- **SMBv1-haavoittuvuudet** mahdollistivat hyökkäykset kuten WannaCry ja NotPetya
- **Dokumenttimakrot** pysyvät ensisijaisena haittaohjelmien toimitustapana
- **USB-pohjaiset hyökkäykset** jatkavat ilmarako-verkkojen kohdistamista
- **PowerShell-väärinkäyttö** on lisääntynyt merkittävästi viime vuosina

## 🛡️ Ghost Turvallisuusfunktiot

Ghost tarjoaa **16 Windows-kovettamisfunktiota** sekä **Azure-turvallisuusintegraation**:

### Windows Päätelaitteen Kovettaminen

| Funktio | Tarkoitus | Huomioitavaa |
|---------|-----------|--------------|
| `Set-RDP` | Hallinnoi etätyöpöytäyhteyttä | Voi vaikuttaa etähallintaan |
| `Set-SMBv1` | Hallitsee vanhaa SMB-protokollaa | Vaaditaan hyvin vanhoissa järjestelmissä |
| `Set-AutoRun` | Hallitsee AutoPlay/AutoRun-toimintoa | Voi vaikuttaa käyttömukavuuteen |
| `Set-USBStorage` | Rajoittaa USB-tallennuslaitteita | Voi vaikuttaa lailliseen USB-käyttöön |
| `Set-Macros` | Hallitsee Office-makrojen suoritusta | Voi vaikuttaa makro-käytössä oleviin dokumentteihin |
| `Set-PSRemoting` | Hallinnoi PowerShell-etäyhteyksiä | Voi vaikuttaa etähallintaan |
| `Set-WinRM` | Hallitsee Windows Remote Managementia | Voi vaikuttaa etähallintaan |
| `Set-LLMNR` | Hallinnoi nimenselvitysprotokollaa | Yleensä turvallista poistaa käytöstä |
| `Set-NetBIOS` | Hallitsee NetBIOS:ia TCP/IP:n yli | Voi vaikuttaa vanhoihin sovelluksiin |
| `Set-AdminShares` | Hallinnoi hallinnollisia jakoja | Voi vaikuttaa etätiedostojen käyttöön |
| `Set-Telemetry` | Hallitsee tiedonkeruuta | Voi vaikuttaa diagnostiikkaominaisuuksiin |
| `Set-GuestAccount` | Hallinnoi vierastiliä | Yleensä turvallista poistaa käytöstä |
| `Set-ICMP` | Hallitsee ping-vastauksia | Voi vaikuttaa verkon diagnostiikkaan |
| `Set-RemoteAssistance` | Hallinnoi etäapua | Voi vaikuttaa help desk -toimintoihin |
| `Set-NetworkDiscovery` | Hallitsee verkon etsintää | Voi vaikuttaa verkon selaamiseen |
| `Set-Firewall` | Hallinnoi Windows-palomuuria | Kriittinen verkon turvallisuudelle |

### Azure Pilviturvallisuus

| Funktio | Tarkoitus | Vaatimukset |
|---------|-----------|-------------|
| `Set-AzureSecurityDefaults` | Mahdollistaa Azure AD:n perusturvallisuuden | Microsoft Graph -oikeudet |
| `Set-AzureConditionalAccess` | Konfiguroi pääsykäytäntöjä | Azure AD P1/P2 -lisenssit |
| `Set-AzurePrivilegedUsers` | Auditoi etuoikeutettuja tilejä | Yleishallinnan oikeudet |

### Yrityksen Käyttöönotto-optiot

| Menetelmä | Käyttötapaus | Vaatimukset |
|-----------|--------------|-------------|
| **Suora Suoritus** | Testaus, pienet ympäristöt | Paikalliset järjestelmänvalvojan oikeudet |
| **Group Policy** | Toimialueympäristöt | Toimialueen järjestelmänvalvoja, GP-hallinta |
| **Microsoft Intune** | Pilvihallinnoitavat laitteet | Intune-lisenssit, Graph API |

## 🚀 Pika-aloitus

### Turvallisuusarviointi
```powershell
# Lataa Ghost-moduuli
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')

# Tarkista nykyinen turvallisuusasema
Get-Ghost
```

### Peruskovettaminen (Testaa Ensin)
```powershell
# Oleellinen kovettaminen - testaa ensin laboratorioympäristössä
Set-Ghost -SMBv1 -AutoRun -Macros

# Tarkista muutokset
Get-Ghost
```

### Yrityksen Käyttöönotto
```powershell
# Group Policy -käyttöönotto (toimialueympäristöt)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Intune-käyttöönotto (pilvihallinnoitavat laitteet)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Asennusmenetelmät

### Vaihtoehto 1: Suora Lataus (Testaus)
```powershell
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')
```

### Vaihtoehto 2: Moduulin Asennus
```powershell
# Asenna PowerShell Gallerysta (kun saatavilla)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Vaihtoehto 3: Yrityksen Käyttöönotto
```powershell
# Kopioi verkkosijaintiin Group Policy -käyttöönottoa varten
# Konfiguroi Intune PowerShell -skriptit pilvikäyttöönottoa varten
```

## 💼 Käyttötapausesimerkit

### Pienyritys
```powershell
# Perussuojaus minimaalisella vaikutuksella
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Terveydenhuoltoympäristö
```powershell
# HIPAA-keskittynyt kovettaminen
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Rahoituspalvelut
```powershell
# Korkean turvallisuuden konfiguraatio
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Pilvi-ensisijainen Organisaatio
```powershell
# Intune-hallinnoitu käyttöönotto
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 📝 Funktioiden Yksityiskohdat

### Keskeiset Kovettamisfunktiot

#### Verkkopalvelut
- **RDP**: Estää etätyöpöytäyhteyden tai satunnaistaa portin
- **SMBv1**: Poistaa käytöstä vanhan tiedostonjakoprotokolla
- **ICMP**: Estää ping-vastaukset tiedustelua varten
- **LLMNR/NetBIOS**: Estää vanhat nimenselvitysprotokollat

#### Sovelluksien Turvallisuus
- **Makrot**: Poistaa käytöstä makrojen suorituksen Office-sovelluksissa
- **AutoRun**: Estää automaattisen suorituksen siirrettävistä medioista

#### Etähallinta
- **PSRemoting**: Poistaa käytöstä PowerShell-etäistunnot
- **WinRM**: Pysäyttää Windows Remote Managementin
- **Etäapu**: Estää etäapuyhteydet

#### Pääsynhallinta
- **Järjestelmänvalvojan Jaot**: Poistaa käytöstä C$, ADMIN$ -jaot
- **Vierastili**: Poistaa käytöstä vierastilin pääsyn
- **USB-tallenteet**: Rajoittaa USB-laitteiden käyttöä

### Azure-integraatio
```powershell
# Yhdistä Azure-vuokralaiseen
Connect-AzureGhost -Interactive

# Ota käyttöön turvallisuusoletukset
Set-AzureSecurityDefaults -Enable

# Konfiguroi ehdollinen pääsy
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Auditoi etuoikeutettuja käyttäjiä
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune-integraatio (Uutta v2:ssa)
```powershell
# Yhdistä Intuneen
Connect-IntuneGhost -Interactive

# Ota käyttöön Intune-käytäntöjen kautta
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Tärkeät Huomioitavat Asiat

### Testausvaatimukset
- **Laboratorioympäristö**: Testaa kaikki asetukset ensin eristetyssä ympäristössä
- **Vaiheittainen Käyttöönotto**: Ota käyttöön vähitellen ongelmien tunnistamiseksi
- **Peruutussuunnitelma**: Varmista, että voit peruuttaa muutokset tarvittaessa
- **Dokumentointi**: Kirjaa ylös, mitkä asetukset toimivat ympäristössäsi

### Mahdollinen Vaikutus
- **Käyttäjien Tuottavuus**: Jotkin asetukset voivat vaikuttaa päivittäisiin työnkulkuihin
- **Vanhat Sovellukset**: Vanhemmat järjestelmät saattavat vaatia tiettyjä protokollia
- **Etäyhteys**: Harkitse vaikutusta lailliseen etähallintaan
- **Liiketoimintaprosessit**: Varmista, että asetukset eivät riko kriittisiä toimintoja

### Turvallisuuden Rajoitukset
- **Syvyyssuoja**: Ghost on yksi turvallisuuskerros, ei täydellinen ratkaisu
- **Jatkuva Hallinta**: Turvallisuus vaatii jatkuvaa seurantaa ja päivityksiä
- **Käyttäjäkoulutus**: Tekniset kontrollit on yhdistettävä turvallisuustietoisuuteen
- **Uhkien Kehitys**: Uudet hyökkäysmenetelmät voivat kiertää nykyiset suojaukset

## 🎯 Esimerkki Hyökkäysskenaarioita

Vaikka Ghost kohdistaa yleisiä hyökkäysvektoreita, spesifi ehkäisy riippuu oikeasta toteutuksesta ja testauksesta:

### WannaCry-tyyppiset Hyökkäykset
- **Lieventäminen**: `Set-Ghost -SMBv1` poistaa käytöstä haavoittuvan protokollan
- **Huomioitavaa**: Varmista, että mikään vanha järjestelmä ei vaadi SMBv1:tä

### RDP-pohjaiset Kiristysohjelmat
- **Lieventäminen**: `Set-Ghost -RDP` estää etätyöpöytäyhteyden
- **Huomioitavaa**: Saattaa vaatia vaihtoehtoisia etäyhteysmetodeja

### Dokumenttipohjaiset Haittaohjelmat
- **Lieventäminen**: `Set-Ghost -Macros` poistaa käytöstä makrojen suorituksen
- **Huomioitavaa**: Saattaa vaikuttaa laillisiin makro-käytössä oleviin dokumentteihin

### USB-toimitetut Uhat
- **Lieventäminen**: `Set-Ghost -USBStorage -AutoRun` rajoittaa USB-toiminnallisuutta
- **Huomioitavaa**: Saattaa vaikuttaa lailliseen USB-laitteiden käyttöön

## 🏢 Yritysominaisuudet

### Group Policy -tuki
```powershell
# Sovella asetukset Group Policy -rekisterin kautta
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Asetukset otetaan käyttöön toimialuelaajuisesti GP-päivityksen jälkeen
gpupdate /force
```

### Microsoft Intune -integraatio
```powershell
# Luo Intune-käytäntöjä Ghost-asetuksille
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Käytännöt otetaan käyttöön automaattisesti hallinnoiduissa laitteissa
```

### Vaatimustenmukaisuusraportointi
```powershell
# Luo turvallisuusarviointiraportti
Get-Ghost | Export-Csv -Path "TurvallisuusAuditointi-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure-turvallisuusaseman raportti
Get-AzureGhost | Out-File "AzureTurvallisuusRaportti.txt"
```

## 📚 Parhaat Käytännöt

### Käyttöönotto-edeltävät
1. **Dokumentoi Nykyinen Tila**: Suorita `Get-Ghost` ennen muutoksia
2. **Testaa Perusteellisesti**: Validoi ei-tuotantoympäristössä
3. **Suunnittele Peruutus**: Tiedä, kuinka kukin asetus peruutetaan
4. **Sidosryhmien Tarkistus**: Varmista, että liiketoimintayksiköt hyväksyvät muutokset

### Käyttöönoton Aikana
1. **Vaiheittainen Lähestymistapa**: Ota käyttöön ensin pilottiryhmissä
2. **Seuraa Vaikutusta**: Tarkkaile käyttäjien valituksia tai järjestelmäongelmia
3. **Dokumentoi Ongelmat**: Kirjaa kaikki ongelmat tulevaa viitettä varten
4. **Viesti Muutoksista**: Tiedota käyttäjille turvallisuusparannuksista

### Käyttöönoton Jälkeen
1. **Säännöllinen Arviointi**: Suorita `Get-Ghost` säännöllisesti asetusten tarkistamiseksi
2. **Päivitä Dokumentaatio**: Pidä turvallisuuskonfiguraatiot ajan tasalla
3. **Arvioi Tehokkuutta**: Seuraa turvallisuusincidenttejä
4. **Jatkuva Parantaminen**: Säädä asetuksia uhkaympäristön perusteella

## 🔧 Vianmääritys

### Yleiset Ongelmat
- **Käyttöoikeusvirheet**: Varmista korotettu PowerShell-istunto
- **Palvelun Riippuvuudet**: Joillakin palveluilla saattaa olla riippuvuuksia
- **Sovellusyhteensopivuus**: Testaa liiketoimintasovelluksilla
- **Verkkoyhteys**: Tarkista, että etäyhteys toimii edelleen

### Palautusvaihtoehdot
```powershell
# Ota käyttöön tietyt palvelut tarvittaessa
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Tekijästä

**Jim Tyler** - Microsoft MVP PowerShellille
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10 000+ tilaajaa)
- **Uutiskirje**: [PowerShell.News](https://powershell.news) - Viikoittainen turvallisuustiedustelu
- **Kirjoittaja**: "PowerShell for Systems Engineers"
- **Kokemus**: Vuosikymmeniä PowerShell-automaatiota ja Windows-turvallisuutta

## 📄 Lisenssi & Vastuuvapauslauseke

### MIT-lisenssi
Ghost toimitetaan MIT-lisenssin alla vapaaseen käyttöön, muokkaukseen ja jakeluun.

### Turvallisuuden Vastuuvapauslauseke
- **Ei Takuuta**: Ghost toimitetaan "sellaisenaan" ilman minkäänlaista takuuta
- **Testaus Vaaditaan**: Testaa aina ensin ei-tuotantoympäristöissä
- **Ammattimainen Ohjaus**: Konsultoi turvallisuusammattilaisia tuotantokäyttöönotoissa
- **Toiminnallinen Vaikutus**: Tekijät eivät ole vastuussa toiminnallisista häiriöistä
- **Kattava Turvallisuus**: Ghost on yksi osa täydellistä turvallisuusstrategiaa

### Tuki
- **GitHub Issues**: [Raportoi bugeja tai pyydä ominaisuuksia](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentaatio**: Käytä `Get-Help <funktio> -Full` yksityiskohtaista apua varten
- **Yhteisö**: PowerShell- ja turvallisuusyhteisön foorumit

---

**🔒 Vahvista turvallisuusasemaasi Ghostilla - mutta testaa aina ensin.**

```powershell
# Aloita arvioinnilla, ei oletuksilla
Get-Ghost
```

**⭐ Anna tälle repositorylle tähti, jos Ghost auttaa parantamaan turvallisuusasemaasi!**