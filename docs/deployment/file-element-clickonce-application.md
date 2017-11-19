---
title: '&lt;plik&gt; elementu (aplikacji ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
caps.latest.revision: "24"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f448b7455bcbe13b7257a58a0eafbadd1165b197
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;plik&gt; elementu (aplikacji ClickOnce)
Identyfikuje wszystkie pliki nonassembly pobrane i używane przez aplikację.  
  
## <a name="syntax"></a>Składnia  
  
```  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `file` Element jest opcjonalny. Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Wymagany. Określa nazwę pliku.|  
|`size`|Wymagany. Określa rozmiar w bajtach pliku.|  
|`group`|Opcjonalny, w przypadku `optional` atrybut jest określony lub nie ustawiono `false`; Jeśli wymagane `optional` jest `true`. Nazwa grupy, do której należy ten plik. Nazwa może być dowolną wartością ciągu Unicode, wybierany przez projektanta i służy do pobierania plików na żądanie z <xref:System.Deployment.Application.ApplicationDeployment> klasy.|  
|`optional`|Opcjonalny. Określa, czy ten plik musi uruchomić pobieranie, gdy aplikacja jest pierwszym lub czy plik powinien znajdować się tylko na serwerze do momentu aplikacja żąda ją na żądanie. Jeśli `false` lub niezdefiniowana, plik jest pobierany podczas najpierw uruchomić lub zainstalować aplikacji. Jeśli `true`, `group` musi być określona dla manifest aplikacji jest nieprawidłowy. `optional`nie może mieć wartości true Jeśli `writeableType` zostanie określony z wartością `applicationData`.|  
|`writeableType`|Opcjonalny. Określa, że ten plik jest plikiem danych. Obecnie jest jedyną poprawną wartością `applicationData`.|  
  
## <a name="typelib"></a>biblioteki typów  
 `typelib` Element jest opcjonalny podrzędnego elementu pliku. Element opisuje biblioteki typów, który należy do składnika modelu COM. Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`tlbid`|Wymagany. Identyfikator GUID przypisane do biblioteki typów.|  
|`version`|Wymagany. Numer wersji biblioteki typów.|  
|`helpdir`|Wymagany. Katalog zawierający pliki pomocy dla składnika. Może być pusty.|  
|`resourceid`|Opcjonalny. Reprezentacja ciągu szesnastkowego identyfikator ustawień regionalnych (LCID). Jest 1 do 4 cyfr szesnastkowych bez prefiksu 0 x i zera wiodące. Identyfikator LCID może mieć identyfikator odmianą niezależnym od języka.|  
|`flags`|Opcjonalny. Reprezentacja ciągu flagi biblioteki typów dla tego typu biblioteki. W szczególności powinien być jednym z "RESTRICTED", "CONTROL", "HIDDEN" i "HASDISKIMAGE".|  
  
## <a name="comclass"></a>comClass  
 `comClass` Element jest opcjonalny element podrzędny `file` elementu, ale jest wymagany, jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik COM zamierza wdrażanie przy użyciu bez rejestrowania modelu COM. Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`clsid`|Wymagany. Identyfikator klasy składnika modelu COM, wyrażony jako identyfikator GUID.|  
|`description`|Opcjonalny. Nazwa klasy.|  
|`threadingModel`|Opcjonalny. Model wątkowości używane przez klasy COM w procesie. Jeśli ta właściwość ma wartość null, jest używany bez modelu wątkowości. Składnik jest tworzony w głównym wątku klienta i wywołania z innych wątków są przekazywane do tego wątku. Na poniższej liście przedstawiono prawidłowe wartości:<br /><br /> `Apartment`, `Free`, `Both`, i `Neutral`.|  
|`tlbid`|Opcjonalny. Identyfikator GUID dla biblioteki typów dla tego składnika COM.|  
|`progid`|Opcjonalny. Identyfikator programowy zależnym od wersji skojarzony z składnik modelu COM. Format `ProgID` jest `<vendor>.<component>.<version>`.|  
|`miscStatus`|Opcjonalny. Informacje dostarczane przez manifest duplikaty w zestawie `MiscStatus` klucza rejestru. Jeśli wartości `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, lub `miscStatusThumbnail` nie znaleziono atrybutów, do odpowiadającej jej wartości domyślnej na liście `miscStatus` jest używana w przypadku brakujących atrybutów. Wartość może być rozdzielana przecinkami lista wartości atrybutów z poniższej tabeli. Można użyć tego atrybutu, jeśli klasa COM jest klasą OCX, która wymaga `MiscStatus` wartości klucza rejestru.|  
|`miscStatusIcon`|Opcjonalny. Duplikaty w zestawie manifestu informacji dostarczonych przez DVASPECT_ICON. Umożliwia ona ikona obiektu. Wartość może być rozdzielana przecinkami lista wartości atrybutów z poniższej tabeli. Można użyć tego atrybutu, jeśli klasa COM jest klasą OCX, która wymaga `Miscstatus` wartości klucza rejestru.|  
|`miscStatusContent`|Opcjonalny. Duplikaty w zestawie manifestu informacji dostarczonych przez DVASPECT_CONTENT. Zapewniają złożonego dokumentu, którą można wyświetlić ekranu lub drukarki. Wartość może być rozdzielana przecinkami lista wartości atrybutów z poniższej tabeli. Można użyć tego atrybutu, jeśli klasa COM jest klasą OCX, która wymaga `MiscStatus` wartości klucza rejestru.|  
|`miscStatusDocPrint`|Opcjonalny. Duplikaty w zestawie manifestu informacji dostarczonych przez DVASPECT_DOCPRINT. Umożliwia ona reprezentację obiektu w postaci wyświetlanej na ekranie tak, jakby drukowania na drukarce. Wartość może być rozdzielana przecinkami lista wartości atrybutów z poniższej tabeli. Można użyć tego atrybutu, jeśli klasa COM jest klasą OCX, która wymaga `MiscStatus` wartości klucza rejestru.|  
|`miscStatusThumbnail`|Opcjonalny. Duplikaty w zestawie manifestu informacji dostarczonych przez DVASPECT_THUMBNAIL. Umożliwia ona miniaturę, którą można wyświetlić w narzędziu do przeglądania obiektu. Wartość może być rozdzielana przecinkami lista wartości atrybutów z poniższej tabeli. Można użyć tego atrybutu, jeśli klasa COM jest klasą OCX, która wymaga `MiscStatus` wartości klucza rejestru.|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 `comInterfaceExternalProxyStub` Element jest opcjonalny element podrzędny `file` elementu, ale może być wymagane w przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik COM zamierza wdrażanie przy użyciu bez rejestrowania modelu COM. Element zawiera następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`iid`|Wymagany. Interfejs identyfikator (IID), która jest obsługiwana przez ten serwer proxy. Identyfikator IID musi mieć nawiasy wokół niej.|  
|`baseInterface`|Opcjonalny. Uzyskanie identyfikatora IID interfejsu, z którego odwołuje się interfejs `iid` pochodzi.|  
|`numMethods`|Opcjonalny. Liczba metod zaimplementowanych przez interfejs.|  
|`name`|Opcjonalny. Nazwa interfejsu, ponieważ będą wyświetlane w kodzie.|  
|`tlbid`|Opcjonalny. Biblioteki typów, zawierający opis interfejsu określonego przez `iid` atrybutu.|  
|`proxyStubClass32`|Opcjonalny. Mapuje IID identyfikatora CLSID obiektu proxy 32-bitowych bibliotek DLL.|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 `comInterfaceProxyStub` Element jest opcjonalny element podrzędny `file` elementu, ale może być wymagane w przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik COM zamierza wdrażanie przy użyciu bez rejestrowania modelu COM. Element zawiera następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`iid`|Wymagany. Interfejs identyfikator (IID), która jest obsługiwana przez ten serwer proxy. Identyfikator IID musi mieć nawiasy wokół niej.|  
|`baseInterface`|Opcjonalny. Uzyskanie identyfikatora IID interfejsu, z którego odwołuje się interfejs `iid` pochodzi.|  
|`numMethods`|Opcjonalny. Liczba metod zaimplementowanych przez interfejs.|  
|`Name`|Opcjonalny. Nazwa interfejsu, ponieważ będą wyświetlane w kodzie.|  
|`Tlbid`|Opcjonalny. Biblioteki typów, zawierający opis interfejsu określonego przez `iid` atrybutu.|  
|`proxyStubClass32`|Opcjonalny. Mapuje IID identyfikatora CLSID obiektu proxy 32-bitowych bibliotek DLL.|  
|`threadingModel`|Opcjonalny. Opcjonalny. Model wątkowości używane przez klasy COM w procesie. Jeśli ta właściwość ma wartość null, jest używany bez modelu wątkowości. Składnik jest tworzony w głównym wątku klienta i wywołania z innych wątków są przekazywane do tego wątku. Na poniższej liście przedstawiono prawidłowe wartości:<br /><br /> `Apartment`, `Free`, `Both`, i `Neutral`.|  
  
## <a name="windowclass"></a>windowClass  
 `windowClass` Element jest opcjonalny element podrzędny `file` elementu, ale może być wymagane w przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik COM zamierza wdrażanie przy użyciu bez rejestrowania modelu COM. Element odwołuje się do klasy okna zdefiniowane przez składnik modelu COM, który musi mieć wersję zastosować dla niego. Element zawiera następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`versioned`|Opcjonalny. Określa, czy okno wewnętrzny klasy nazwę używaną w rejestracji zawiera wersję zestawu zawierającego klasę okna kontrolki. Wartość tego atrybutu może być `yes` lub `no`. Wartość domyślna to `yes`. Wartość `no` należy używać tylko w przypadku tej samej klasy okna jest definiowany przez side-by-side i równoważne składnik nie side-by-side i chcesz je traktować jako tej samej klasy okna. Należy pamiętać, że zwykle reguły o rejestrowanie klasy okna — tylko pierwszy składnik, który rejestruje klasę okna będą mogli zarejestrować go, ponieważ nie ma wersji zastosować dla niego.|  
  
## <a name="hash"></a>hash  
 `hash` Element jest opcjonalny element podrzędny `file` elementu. `hash` Element nie ma żadnych atrybutów.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]używa algorytmicznego skrót wszystkich plików w aplikacji w celu sprawdzenia zabezpieczeń, aby upewnić się, że żadne pliki nie zostały zmieniły po wdrożeniu. Jeśli `hash` element nie jest dołączana, to sprawdzenie nie zostanie wykonane. W związku z tym pominięcie `hash` element nie jest zalecane.  
  
 Jeśli manifestu zawiera plik, który nie jest wartość skrótu, że manifestu nie może być cyfrowo podpisać, ponieważ użytkownicy nie może zweryfikować zawartości pliku bez haszowania.  
  
## <a name="dsigtransforms"></a>DSIG:TRANSFORMS  
 `dsig:Transforms` Element jest elementem podrzędnym wymagane `hash` elementu. `dsig:Transforms` Element nie ma żadnych atrybutów.  
  
## <a name="dsigtransform"></a>DSIG:Transform  
 `dsig:Transform` Element jest elementem podrzędnym wymagane `dsig:Transforms` elementu. `dsig:Transform` Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Algorithm`|Algorytm używany do obliczania skrótu dla tego pliku. Obecnie tylko wartość używana przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>DSIG:DigestMethod  
 `dsig:DigestMethod` Element jest elementem podrzędnym wymagane `hash` elementu. `dsig:DigestMethod` Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Algorithm`|Algorytm używany do obliczania skrótu dla tego pliku. Obecnie tylko wartość używana przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>DSIG:DigestValue  
 `dsig:DigestValue` Element jest elementem podrzędnym wymagane `hash` elementu. `dsig:DigestValue` Element nie ma żadnych atrybutów. Wartość tekstu jest obliczona wartość skrótu dla określonego pliku.  
  
## <a name="remarks"></a>Uwagi  
 Ten element określa wszystkie pliki nonassembly wchodzące w skład aplikacji i, w szczególności wartości skrótu dla pliku weryfikacji. Ten element może także zawierać dane izolacji składnika modelu COM (Object) skojarzone z plikiem. W przypadku zmiany pliku, plik manifestu aplikacji również musi zaktualizować celu odzwierciedlenia zmian.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `file` elementów w aplikacji manifestu dla aplikacji wdrożone przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)