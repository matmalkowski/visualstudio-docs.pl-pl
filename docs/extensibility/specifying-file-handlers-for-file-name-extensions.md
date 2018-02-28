---
title: "Określanie obsługi pliku rozszerzenia nazw plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d5db7a218a718e27f584abbf350b49907b56fb17
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Określanie obsługi pliku rozszerzenia nazw plików
Istnieje wiele sposobów, aby określić aplikację, która obsługuje pliku, który ma rozszerzenie określonego pliku. Zleceń OpenWithList i OpenWithProgids są dwa sposoby określania obsługi pliku w obszarze wpis rejestru dla rozszerzenia pliku.  
  
## <a name="openwithlist-verb"></a>Zlecenie OpenWithList  
 Po kliknięciu prawym przyciskiem myszy plik w Eksploratorze Windows, temacie **Otwórz** polecenia. Jeśli więcej niż jeden produkt jest skojarzona z rozszerzeniem, zobacz **Otwórz za pomocą** podmenu.  
  
 Możesz zarejestrować się różne aplikacje, aby otworzyć rozszerzenie ustawiając klucz OpenWithList dla rozszerzenia pliku w wpisów z HKEY_CLASSES_ROOT. Aplikacje w tym kluczu dla rozszerzenia pliku na liście są wyświetlane w obszarze **zalecane programy** nagłówek w **Otwórz za pomocą** okno dialogowe. Poniższy przykład przedstawia aplikacji, w zarejestrowany w celu otwarcia .vcproj rozszerzenie pliku.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Określanie aplikacji są klucze z listy w obszarze HKEY_CLASSES_ROOT\Applications.  
  
 Dodawanie klucza OpenWithList, zadeklarować, czy aplikacja obsługuje rozszerzenie pliku, nawet wtedy, gdy inna aplikacja ma prawo własności do rozszerzenia. Może to być przyszłych wersji aplikacji lub innej aplikacji.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 Identyfikatory programowe (ProgID) są przyjazne wersje klasy, które zidentyfikować wersji aplikacji lub obiektu COM. Każdy obiekt wspólnie możliwość utworzenia powinny mieć własny identyfikator ProgID. Na przykład VisualStudio.DTE.7.1 uruchamia program Visual Studio .NET 2003, podczas uruchamiania VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Jako właściciel typu projektu lub typu elementu projektu należy utworzyć ProgID określonej wersji dla rozszerzenia pliku. Te ProgID może być nadmiarowego, w tym więcej niż jeden identyfikator ProgID może rozpocząć tej samej aplikacji. Aby uzyskać więcej informacji, zobacz [rejestrowania poleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Aby uniknąć duplikowania rejestracji innych dostawców, użyj następującej konwencji nazewnictwa dla określonej wersji pliku ProgID:  
  
|Rozszerzenie pliku|Kontrolą wersji ProgID|  
|--------------------|----------------------|  
|.Extension|NazwaProduktu. extension.versionMajor.versionMinor|  
  
 Możesz zarejestrować różne aplikacje, które można otworzyć rozszerzenie pliku określonego przez dodanie numerów wersji ProgID jako wartości wpisów z HKEY_CLASSES_ROOT\\*\<rozszerzenia >*\OpenWithProgids klucza. Ten klucz rejestru zawiera listę alternatywnej ProgID skojarzonego z rozszerzeniem pliku. Aplikacje skojarzone z wymienionych ProgID pojawiają się w **Otwórz za pomocą***nazwa produktu* podmenu. Jeśli ta sama aplikacja jest określony zarówno `OpenWithList` i `OpenWithProgids` kluczy, system operacyjny scala duplikaty.  
  
> [!NOTE]
>  `OpenWithProgids` Kluczy jest obsługiwana tylko w systemie Windows XP. Ponieważ inne systemy operacyjne zignorować ten klucz, nie używać go jako tylko rejestracji obsługi pliku. Ten klucz umożliwia lepsze środowisko pracy użytkownika w systemie Windows XP.  
  
 Dodaj odpowiednie ProgID jako wartości typu REG_NONE. Poniższy kod stanowi przykład rejestrowania ProgID rozszerzenie pliku (. *Roz*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Identyfikator ProgID określony jako domyślny program obsługi pliku jest wartością domyślną dla rozszerzenia pliku. Jeśli zmodyfikujesz identyfikatora rozszerzenie, które zostały wydane z poprzedniej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub które mogą zostać przejęte inne aplikacje, a następnie zarejestruj `OpenWithProgids` klucz dla rozszerzenia pliku i określ nowy identyfikator ProgID na liście wraz z programem stary ProgID, która jest obsługiwana. Na przykład:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Jeśli stary ProgID ma skojarzone z nim zlecenia, a następnie te zleceń pojawi się również w obszarze **Otwórz za pomocą** *nazwa produktu* w menu skrótów.  
  
## <a name="see-also"></a>Zobacz też  
 [Temat rozszerzeń nazw plików](../extensibility/about-file-name-extensions.md)   
 [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)