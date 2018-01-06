---
redirect_url: shell/visual-studio-shell-integrated
title: Visual Studio Shell (zintegrowany) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b43e4ac1c8e40a9f4f378be42cc642767bee0777
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (zintegrowany)
Powłoka programu Visual Studio zintegrowane obejmują zintegrowane środowisko programistyczne (IDE), debuger i integracji kontroli źródła. Nie język programowania jest dołączony. Powłoka w trybie zintegrowanym zapewnia jednak platforma, która pozwala na dodawanie języków programowania.  
  
 Powłoki programu Visual Studio zintegrowane jest rzeczywiście kombinację powłoki programu Visual Studio izolowane oraz instalację dodatkowych obejmujące powłoka w trybie zintegrowanym określone składniki.  Powłoka w trybie zintegrowanym aplikacji powinna zawierać zarówno programu isolated shell pakiet redystrybucyjny programu z [pakiet redystrybucyjny programu Microsoft Visual Studio Shell (izolowany)](http://go.microsoft.com/fwlink/?LinkId=616022) oraz pakiet redystrybucyjny powłoka w trybie zintegrowanym z [programu Microsoft Visual Studio powłoki (zintegrowany) pakietu redystrybucyjnego](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Przed uzyskaniem dostępu pakiety redystrybucyjne izolowanej i zintegrowane powłoki, poprosimy Cię o ankiety krótki klienta.  Po wypełnieniu ankiety, nastąpi przekierowanie do strony Połącz program Visual Studio z łącza pobierania pakietu redystrybucyjnego.  Łącza pobierania przy kolejnych wizytach do witryny Visual Studio Connect w obszarze **programy &#124; VISUAL STUDIO 2015 zintegrowanego i ISOLATED SHELL** kartę.  
  
 Po zainstalowaniu aplikacji powłoka w trybie zintegrowanym na tym samym komputerze co pełną wersję programu Visual Studio zintegrowania składniki aplikacji bezpośrednio do programu Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Funkcje powłoka w trybie zintegrowanym  
  
|||  
|-|-|  
|Obszar funkcji|Funkcja|  
|Obsługa języków|-Brak|  
|IDE|<ul><li>Ustawienia<br /><br /> <ul><li>Tworzenie ustawień</li><li>Import i eksport ustawień</li><li>Zresetuj ustawienia</li></ul></li><li>**Przybornik** integracji</li><li>**Lista zadań** integracji</li><li>Pomoc w integracji</li><li>**Opcje** — okno dialogowe</li><li>Czcionki i kolory zarządzania</li><li>**Dane wyjściowe** okna</li><li>**Polecenie** okna</li><li>Zarządzanie oknem</li><li>Polecenia, menu i powiązań klucza</li><li>Środowisko uruchomieniowe języka specyficznego dla domeny (DSL)</li></ul>|  
|System projektu i typy projektów|— Rozwiązania i rozwiązanie<br />— Menedżer konfiguracji rozwiązania<br />— Zarządzanie element<br />— Rozwiązania pojedynczych projektów i wielu projektów<br />-Projektant aplikacji (właściwości projektu uproszczony)<br />-Dodaj odwołanie sieci Web<br />-Dodaj odwołanie do usługi<br />Pojedynczych projektów<br />— Typy projektów witryny sieci Web<br />— Projekty aplikacji sieci web|  
|Kompilacja|-Niestandardowe kroki procesu kompilacji w środowisku IDE<br />-Wstępnej kompilacji do ochrony własności intelektualnej (IP)<br />-Podpisywanie kodu<br />     MSBuild|  
|Edytor|-Narzędzia (Znajdź ujednoliconą, definicji źródła, dziedziczenia) przeglądania kodu<br />— Nawigacja kod<br />-IntelliSense<br />-Tagi inteligentne<br />-Refaktoryzacji<br />-Pretty listy<br />-Filtrowanie IntelliSense<br />-   **Kod definicji** okna|  
|Projektant|— Windows Presentation Foundation projektanta<br />-Projektant formularzy systemu Windows<br />-Sieci web projektanta i edytora HTML|  
|Dane|-   **W Eksploratorze serwera** (uproszczony: tylko dane). Patrz Uwaga 1.<br />-   **Źródła danych** okna<br />-Pełny zestaw danych formantów<br />— Edytor XML<br />-Data powiązać z lokalnego źródła danych (. MDF lub. MDB)<br />-Data bind do obiektu<br />-Powiązanie danych usługą sieci Web<br />-Data powiązania do lokalnej bazy danych serwera<br />-Data powiązać serwer zdalnej bazy danych<br />-DDL narzędzi dla danych zdalnych<br />-   **W Eksploratorze serwera** rozszerzalności ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] — przykłady)|  
|Debuger|— Debugowanie lokalne. Patrz Uwaga 2.<br />-Debugowania zarządzanego<br />— Debugowanie lokalne<br />-Dołączyć do procesu lokalnego<br />-Dołączyć do procesu zdalnego<br />-Delegat anonimowe<br />-Domeny aplikacji<br />— Debugowanie ASPX<br />— Atrybuty<br />-Break podczas Func eval<br />-Punkty przerwania<br />— Ograniczenia punkt przerwania<br />-Stosu wywołań<br />-   **Polecenie** okna<br />— Debugowanie między wątkami<br />— Dane wskazówki<br />-Data wizualizatora<br />— Obsługa debuger Asystenci zarządzanego debugowania (mda)<br />-Obsługa debugera dla usługi przesyłania dalej typu<br />-Obsługa DTEEvents OTB<br />-JMC Stepper<br />-Debugera AppID testu (DBGCLR)<br />— Profil debuger<br />-Debugera, narzędzia i opcje<br />-Iteratora debugowania<br />-Szacowanie wyrażeń czasu projektowania<br />— Ewaluator wyrażeń C#<br />-Dezasemblacji<br />-Edytuj i Kontynuuj<br />— Windows ewaluatora wyrażenie (oglądanie, zmienne lokalne, samochodów)<br />— Pomocnik wyjątek<br />-Wyjątków<br />-Wykonywania<br />— Ogólne<br />— Pobranie prawo źródła<br />— Debugowanie/klastra HPC<br />— Zintegrowane profilowanie obsługi wielu języków.<br />— Debugowanie międzyoperacyjne<br />Debugowanie just-in time<br />— Debugowanie lokalne<br />-Debugowania zarządzanego<br />-Ręcznej kontroli (okno procesów)<br />-Pamięci<br />-Obsługa minizrzutu<br />-Modułów<br />— Debugowanie wieloprocesowa<br />-Debugowanie natywne<br />— Nowa funkcja obsługi aparatu debugowania<br />— Debugowanie zoptymalizowanego kodu<br />-Windows output filtrowania<br />-Przetwarzanie hosting do debugowania zarządzanego<br />-Procesów<br />— Quickwatch<br />-Rejestrów<br />-Rejestruje stosu<br />-Zdalnego debugowania<br />-Zwracanych wartości<br />-Debugowanie skryptów<br />-Obsługa usługi source<br />-Zabezpieczeń<br />Side-by-side<br />-SQL<br />— Serwer symbol<br />-Punkty śledzenia<br />-Wątku<br />-Wizualizacji<br />-Extensible debugera arkusza stylów języka przekształcenia XSLT)|  
|Obsługa 64-bitowego|-debugowania 64-bitowego kodu zarządzane i natywne, wszystkie języki<br />— obsługuje x64 macierzystego|  
|Kontroli kodu źródłowego (SCC)|— Integracja SCC podstawowe. Patrz Uwaga 3.<br />-Narzędzi i opcji weryfikacji|  
|Rozszerzalność|-Korzystać pakiety VSPackage i MEF składników|  
  
## <a name="notes"></a>Uwagi  
  
#### <a name="1-data-tools"></a>1. Narzędzia danych  
 Powłoka w trybie zintegrowanym zawiera bazy danych narzędzi programistycznych, takich jak Obsługa rozszerzeń danych i uproszczone **Eksploratora rozwiązań**. Jednak programu SQL Server Express, SQL Reporting i Crystal Reports nie znajdują się w zintegrowanym powłoki.  
  
#### <a name="2-debugging-support"></a>2. Obsługa debugowania  
 Powłoka w trybie zintegrowanym dotyczy tego samego aparatu debugowania, który znajduje się w wersji Community programu Visual Studio. Aparat debugowania zawiera typowe debuger dla kodu zarządzanego i powiązanych funkcji, takie jak uruchomić, Attach, ustaw punkt przerwania, Edytuj i Kontynuuj i inne. Jednak aparat debugowania nie obsługuje debugowania bazy danych programu SQL Server.  
  
 Mimo że obsługi dla debugowanie natywne jest uwzględniony w pakiecie podstawowe debugera, nie można rozszerzyć je do obsługi dodatkowych języków.  
  
#### <a name="3-source-code-control-integration"></a>3. Integracji kontroli kodu źródłowego  
 Powłoka w trybie zintegrowanym udostępnia interfejsy API do wykonywania kontroli kodu źródłowego (SCC) i udostępnia składników integracji kontroli źródła na podstawie MSSCCI wspólnej.  
  
 Mimo że integracji SCC nie jest funkcją regularne wydanie Pro z programu Visual Studio, integracja SCC znajduje się w powłoka w trybie zintegrowanym.  
  
#### <a name="4-build-support"></a>4. Obsługa kompilacji  
 Powłoka w trybie zintegrowanym zapewnia obsługę kompilacji. Można znaleźć informacje o kompilacji w [odwołanie MSBuild](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Nieuwzględnione w powłoce zintegrowane funkcje  
 Oto lista funkcji, które nie są uwzględnione w zintegrowanym powłoki:  
  
-   Projektant klas  
  
-   [Ochrona cenią sobie wcześniejsze — Dotfuscator](../ide/dotfuscator/index.md)  
  
-   Funkcje językowe  
  
-   VSHost  
  
-   Żadnych języków Visual Studio lub ich szablony projektów skojarzone lub szablony elementów projektu, zostaną uwzględnione w powłoka w trybie zintegrowanym. Żadna implementacja specyficzny dla języka innych funkcji są dołączone do przykładowych fragmentów kodu Visual Basic.  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)