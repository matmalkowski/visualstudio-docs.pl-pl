---
title: Podstawy Instalatora systemu Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8fba35aba1e1947ee4eeeb59ca2225253e2aa3a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144753"
---
# <a name="windows-installer-basics"></a>Podstawy Instalatora systemu Windows
Instalator Windows instaluje i odinstalowuje aplikacje lub programów na komputerze użytkownika wykonywania tych zadań w jednostki nazywane składnikami Instalatora Windows (czasami nazywany WICs lub tylko składniki). Identyfikator GUID identyfikuje każda usługa WIC to podstawowa jednostka instalacji i zliczanie dla konfiguracji za pomocą Instalatora Windows.  
  
 Pełna dokumentacja Instalatora systemu Windows zawiera temat zestawu SDK platformy, [Instalatora Windows](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## <a name="authoring-a-vspackage"></a>Tworzenie pakiet VSPackage  
 Instalator Windows używa pakietów instalacyjnych, które zawierają informacje, które Instalator systemu Windows należy zainstalować, odinstalować lub napraw produkt i uruchamiania Instalatora interfejsu użytkownika (UI). Każdy pakiet instalacyjny zawiera plik msi, który zawiera bazy danych instalacji, strumień informacji podsumowujących i strumieni danych dla różnych części instalacji. Aby użyć Instalatora, należy utworzyć instalacji. Ponieważ Instalator organizuje instalacje myślą o składniki i przechowuje informacje o instalacji relacyjnej bazy danych, proces tworzenia pakietu instalacyjnego szeroko pociąga za sobą następujące czynności:  
  
1.  Planowanie ustawień autorstwa do obsługi przechowywania wersji, a side-by-side strategii.  
  
2.  Identyfikowanie funkcji, które będą widoczne dla użytkowników.  
  
3.  Organizowanie pakiet VSPackage i zależności w składników.  
  
4.  Wypełnianie bazy danych instalacji z informacjami.  
  
5.  Sprawdzanie poprawności pakietu instalacyjnego.  
  
 Ta dokumentacja dotyczy głównie pierwszy i trzeci etapy procesu. Podczas tych czynności możesz organizować funkcje pakiet VSPackage w WICs, można ramki Twojej wersji i obsługi konta w kolejnych wersjach strategii [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Trzy pozostałe kroki są zostały szczegółowo opisane w dokumentacji systemu Windows w zestawie SDK platformy.  
  
## <a name="key-terms"></a>Kluczowe terminy  
 Poniżej znajdują się definicje kluczowe terminy związane z technologii Instalatora systemu Windows.  
  
 Zasób  
 Pliki, klucze rejestru, skrótów lub i tak dalej może być zainstalowana na komputerze. Te zasoby są pogrupowane logicznie w składników Instalatora Windows.  
  
 Instalator Windows component (WIC)  
 Podstawowa jednostka reprezentująca logiczne grupowanie powiązanych zasobów, które są zainstalowane i odinstalować jako jednostka instalacji. Składniki Instalatora systemu Windows są identyfikowane przez identyfikator unikatowy składnika lub identyfikator GUID. Ponadto Instalator systemu Windows zachowuje jego zliczanie na poziomie WIC. Elastyczność maksymalne przechowywanie wersji zawierać nie więcej niż jeden zasób podstawowego, takich jak biblioteki DLL, w danym WIC. Należy pamiętać, że po identyfikacji i wypełnić WIC, nadaj mu identyfikator GUID i wdróż je, nie można zmienić jego kompozycji. Aby uzyskać więcej informacji, zobacz [organizowania aplikacji do składników](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 (Pakiet Redist)  
 Jednostka wdrożenia, który składa się z pliku .msi i zewnętrzne pliki źródłowe, do których może wskazywać tego pliku. Pakiet zawiera wszystkie informacje, które Instalatorowi systemu Windows do uruchamiania interfejsu użytkownika i w celu zainstalowania lub odinstalowania aplikacji.  
  
 plik msi  
 Plik magazynu strukturalnego COM zawierający instrukcje i dane wymagane do zainstalowania aplikacji. Każdy pakiet zawiera co najmniej jeden plik msi. Plik msi zawiera baza danych Instalatora, strumień informacji podsumowujących i prawdopodobnie transformacje co najmniej jednego i wewnętrzne pliki źródłowe. Pliki do zainstalowania można być skompresowane w pliku cabinet i przechowywane w strumieniu w pliku msi lub przechowywane, skompresowane albo nieskompresowane poza plik msi na nośniku źródłowym. Aby uzyskać więcej informacji, zobacz [rozszerzeń plików Instalatora Windows](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Wymuszanie reguł Instalatora Windows  
 Dwa zestawy reguł określają wdrażania zasobów przez składniki programu Instalatora. Jeden zestaw reguł jest obsługiwana przez Instalator systemu Windows, gdy drugi zestaw jako autor instalacja powinna wymuszać.  
  
> [!NOTE]
>  Wymuszania reguł Instalatora Windows występuje tylko w przypadku uruchomienia sprawdzania poprawności pliku msi. Niemniej jednak są cautioned traktować te reguły jako najlepsze rozwiązanie. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności instalacji bazy danych](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) i [sprawdzanie poprawności pakietu](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Wymuszone Instalator reguły  
  
-   Wszystkie pliki w danym składnik musi być zainstalowany na tym samym katalogu. Z drugiej strony pliki zainstalowane na osobnych folderów muszą należeć do oddzielania składników.  
  
-   Może istnieć tylko jedna ścieżka klucza na składnika. Ścieżka klucza jest po prostu plików lub rejestrze klucz, który reprezentuje cały składnika.  
  
#### <a name="component-provider-responsibilities"></a>Obowiązki dostawcy składników  
  
-   Dwa zasoby, które mogą być oddzielnie w kolejnych wersjach muszą istnieć w oddzielnych części. Zasoby powinny zostać utworzone w tym samym składnikiem tylko wtedy, gdy masz pewność, że te zasoby nigdy nie wyśle oddzielnie. W rzeczywistości, zalecane jest wszystkie zasoby podstawowej (na przykład dll) w oddzielnych WICs zawsze istnieć. Aby uzyskać więcej informacji, zobacz [definiowanie składników Instalatora](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Żaden zasób kontrolą wersji powinien wysłać kiedykolwiek w więcej niż jeden WIC.  
  
## <a name="see-also"></a>Zobacz też  
 [Co się stanie, jeśli reguły składników są dzielone?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)