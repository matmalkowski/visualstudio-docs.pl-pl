---
title: "&lt;zależności&gt; elementu (aplikacji ClickOnce) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: "34"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 7c3319661a4c0df298cd844c4d71c6855cad818c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;zależności&gt; elementu (aplikacji ClickOnce)
Identyfikuje platformy lub zestawu zależności, która jest wymagana dla aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
         <hash>  
            <dsig:Transforms>  
               <dsig:Transform  
                  Algorithm  
            />  
            </dsig:Transforms>  
            <dsig:DigestMethod />  
            <dsig:DigestValue>  
            </dsig:DigestValue>  
    </hash>  
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `dependency` Element jest wymagany. Może istnieć wiele wystąpień `dependency` w tym samym manifest aplikacji.  
  
 `dependency` Element nie ma żadnych atrybutów i zawiera następujące elementy podrzędne.  
  
### <a name="dependentos"></a>dependentOS  
 Opcjonalny. Zawiera `osVersionInfo` elementu. `dependentOS` i `dependentAssembly` elementy wykluczają się wzajemnie: jedna z tych musi istnieć dla `dependency` elementu, ale nie oba.  
  
 `dependentOS`obsługuje następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`supportUrl`|Opcjonalny. Określa adres URL pomocy technicznej platformy zależnej. Ten adres URL jest pokazywana użytkownikowi, jeśli zostanie znaleziony wymagane platformy.|  
|`description`|Opcjonalny. W tym artykule opisano, w postaci czytelny dla człowieka opisanego przez system operacyjny `dependentOS` elementu.|  
  
### <a name="osversioninfo"></a>osVersionInfo  
 Wymagany. Ten element jest elementem podrzędnym `dependentOS` element i zawiera `os` elementu. Ten element nie ma żadnych atrybutów.  
  
### <a name="os"></a>system operacyjny  
 Wymagany. Ten element jest elementem podrzędnym `osVersionInfo` elementu. Ten element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`majorVersion`|Wymagany. Określa główny numer wersji systemu operacyjnego.|  
|`minorVersion`|Wymagany. Określa podrzędny numer wersji systemu operacyjnego.|  
|`buildNumber`|Wymagany. Określa numer kompilacji systemu operacyjnego.|  
|`servicePackMajor`|Wymagany. Określa numer główne usługi pakietu systemu operacyjnego.|  
|`servicePackMinor`|Opcjonalny. Określa numer drobne usługi pakietu systemu operacyjnego.|  
|`productType`|Opcjonalny. Określa wartość typu produktu. Prawidłowe wartości to `server`, `workstation`, i `domainController`. Na przykład dla systemu Windows 2000 Professional, ta wartość atrybutu jest `workstation`.|  
|`suiteType`|Opcjonalny. Identyfikuje pakiet produktów, dostępne w systemie lub typ konfiguracji systemu. Prawidłowe wartości to `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted`, i `terminal`. Na przykład dla systemu Windows 2000 Professional, ta wartość atrybutu jest `professional`.|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 Opcjonalny. Zawiera `assemblyIdentity` elementu. `dependentOS` i `dependentAssembly` elementy wykluczają się wzajemnie: jedna z tych musi istnieć dla `dependency` elementu, ale nie oba.  
  
 `dependentAssembly`ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`dependencyType`|Wymagany. Określa typ zależności. Prawidłowe wartości to `preprequisite` i `install`. `install` Zestawu jest instalowany jako część [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. A `prerequisite` zestawu musi znajdować się w globalnej pamięci podręcznej zestawów (GAC) przed [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] można zainstalować aplikacji.|  
|`allowDelayedBinding`|Wymagany. Określa, czy zestaw może być załadowany programowo w czasie wykonywania.|  
|`group`|Opcjonalny. Jeśli `dependencyType` atrybut ma ustawioną `install`, określa grupę nazwane zestawy tylko instalację na żądanie. Aby uzyskać więcej informacji, zobacz [wskazówki: Pobieranie zestawów na żądanie z ClickOnce wdrażania interfejsu API przy użyciu narzędzia Projektant](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Jeśli ustawiono `framework` i `dependencyType` atrybut ma ustawioną `prerequisite`, określa zestaw jako część programu .NET Framework. Podczas instalowania na assemby globalnej pamięci podręcznej (GAC) nie jest zaznaczone dla tego zestawu [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] i nowszych wersjach.|  
|`codeBase`|Wymagany, gdy `dependencyType` atrybut ma ustawioną `install`. Ścieżka do zestawu zależnego. Może być ścieżką bezwzględną lub ścieżką względną wobec kodu manifestu podstawowej. Ta ścieżka musi być prawidłowym identyfikatorem URI w kolejności dla manifest zestawu jest nieprawidłowy.|  
|`size`|Wymagany, gdy `dependencyType` atrybut ma ustawioną `install`. Rozmiar zestawu zależnego w bajtach.|  
  
### <a name="assemblyidentity"></a>element assemblyIdentity  
 Wymagany. Ten element jest elementem podrzędnym `dependentAssembly` element i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Wymagany. Określa nazwę aplikacji.|  
|`version`|Wymagany. Określa numer wersji aplikacji w następującym formacie:`major.minor.build.revision`|  
|`publicKeyToken`|Opcjonalny. Określa ciąg szesnastkowy 16 znaków, który reprezentuje ostatnich 8 bajtów `SHA-1` wartość klucza publicznego, pod którą jest podpisany aplikacji lub zestawu skrótu. Klucz publiczny używany do podpisywania katalogu musi być 2048 bitów lub większej.|  
|`processorArchitecture`|Opcjonalny. Określa procesora. Prawidłowe wartości to `x86` dla 32-bitowego systemu Windows i `I64` dla 64-bitowego systemu Windows.|  
|`language`|Opcjonalny. Identyfikuje części dwóch kodów języków, takich jak pl-pl, zestawu.|  
  
### <a name="hash"></a>hash  
 `hash` Element jest opcjonalny element podrzędny `assemblyIdentity` elementu. `hash` Element nie ma żadnych atrybutów.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]używa algorytmicznego skrót wszystkich plików w aplikacji w celu sprawdzenia zabezpieczeń, aby upewnić się, że żadne pliki nie zostały zmieniły po wdrożeniu. Jeśli `hash` element nie jest dołączana, to sprawdzenie nie zostanie wykonane. W związku z tym pominięcie `hash` element nie jest zalecane.  
  
### <a name="dsigtransforms"></a>DSIG:TRANSFORMS  
 `dsig:Transforms` Element jest elementem podrzędnym wymagane `hash` elementu. `dsig:Transforms` Element nie ma żadnych atrybutów.  
  
### <a name="dsigtransform"></a>DSIG:Transform  
 `dsig:Transform` Element jest elementem podrzędnym wymagane `dsig:Transforms` elementu. `dsig:Transform` Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Algorithm`|Algorytm używany do obliczania skrótu dla tego pliku. Obecnie tylko wartość używana przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### <a name="dsigdigestmethod"></a>DSIG:DigestMethod  
 `dsig:DigestMethod` Element jest elementem podrzędnym wymagane `hash` elementu. `dsig:DigestMethod` Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Algorithm`|Algorytm używany do obliczania skrótu dla tego pliku. Obecnie tylko wartość używana przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### <a name="dsigdigestvalue"></a>DSIG:DigestValue  
 `dsig:DigestValue` Element jest elementem podrzędnym wymagane `hash` elementu. `dsig:DigestValue` Element nie ma żadnych atrybutów. Wartość tekstu jest obliczona wartość skrótu dla określonego pliku.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie zestawy używane przez aplikację muszą mieć odpowiadające mu `dependency` elementu. Zależne zestawy nie zawierają zestawy, które musi być preinstalowany w pamięci podręcznej GAC jako zestawów platformy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `dependency` elementów w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji. Ten przykładowy kod jest częścią większego przykładu udostępnionego dla [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md) tematu.  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<zależności > — Element](../deployment/dependency-element-clickonce-deployment.md)