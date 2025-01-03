# Popis projektu

Projekt se zaměřuje na vývoj API služby pro správu hesel, která umožní bezpečné ukládání, zobrazení, úpravu a sdílení hesel mezi jednotlivci i skupinami uživatelů. Projekt bude zahrnovat návrh a implementaci celé služby včetně základního frontendu pro interakci uživatelů.

# Klíčové funkce  

- **Ukládání hesel:** Uživatelé mohou bezpečně ukládat svá hesla. Každé heslo bude šifrováno před uložením v databázi pomocí šifrovacího algoritmu.  
- **Zobrazení hesel:** Jednotliví uživatelé mohou zobrazit své uložené hesla, či hesla v rámci skupiny, pro které mají práva.
- **Tvorba a úprava hesel:** Uživatelé mohou přidávat nová hesla, upravovat existující, nebo je mazat.  
- **Sdílení hesel:** Uživatelé mohou vytvářet skupiny a sdílet v nich vybraná hesla s dalšími členy. Každý člen bude mít přidělené pravomoci (např. pouze čtení, nebo čtení i editace). 
- **Audit přístupu:** Systém bude zaznamenávat, kdo a kdy přistoupil k jednotlivým heslům, což zajistí přehled o aktivitách ve skupinách.  
- **Jednoduchý frontend:** Základní webová aplikace umožní uživatelům snadno interagovat s API. 

# Využití  

Správce hesel má široké využití jak pro jednotlivce, tak pro týmy či firmy.  
Pro jednotlivce slouží k bezpečnému ukládání a správě hesel na osobní úrovni. 
Pro týmy poskytuje snadný způsob, jak sdílet přístupové údaje například k týmovým účtům nebo firemním systémům, a to s možností detailní kontroly nad tím, kdo má k heslům přístup, co s nimi může dělat a kdy s nimi a jakým způsobem zacházel.  

# Entity

## Uživatel

Tato entita reprezentuje jednotlivého uživatele systému a jeho interakci s API.  

- **Atributy:**  
  - Uživatelské ID (unikátní identifikátor).  
  - Uživatelské jméno.  
  - Emailová adresa.  
  - Role (např. administrátor, běžný uživatel).  
  - Přihlašovací údaje (uložené bezpečně a šifrované).
    
- **Funkce:**  
  - Registrace a přihlášení do systému.  
  - Správa osobních nastavení a profilových údajů.  
  - Přidělování práv pro přístup k heslům nebo skupinám.  

## Skupina 

Tato entita umožňuje vytváření skupin, ve kterých mohou uživatelé sdílet hesla.  

- **Atributy:**  
  - ID skupiny (unikátní identifikátor).  
  - Název skupiny (např. „Marketing Team“).  
  - Seznam členů.  
  - Sdílená hesla.
    
- **Funkce:**  
  - Přidávání nebo odebírání členů.  
  - Správa oprávnění členů (např. pouze čtení, čtení a editace).  
  - Sdílení hesel mezi členy skupiny.  

## Hesla

Entita hesla slouží k ukládání a správě přístupových údajů jednotlivých uživatelů nebo skupin.  

- **Atributy:**  
  - ID hesla (unikátní identifikátor).  
  - Název účtu nebo služby (např. „Gmail“).  
  - Šifrované heslo.  
  - URL nebo poznámka (např. „https://mail.google.com“).  
  - Metadata (datum vytvoření, poslední aktualizace).
    
- **Funkce:**  
  - Ukládání nových hesel.  
  - Úprava a mazání existujících hesel.  
  - Zobrazení hesel autorizovaným uživatelům.  

## Log

Tato entita zajišťuje zaznamenávání všech akcí, které proběhnou v systému.  

- **Atributy:**  
  - ID záznamu (unikátní identifikátor).  
  - Čas akce.  
  - Typ akce (např. „zobrazení hesla“, „úprava hesla“).  
  - Uživatelské ID, které akci provedlo.  
  - Cílová entita (např. konkrétní heslo nebo skupina).
  
- **Funkce:**  
  - Monitoring aktivit v systému.  
  - Poskytování dat pro analýzu a bezpečnostní audity.  
  - Export logů pro správce systému.  
