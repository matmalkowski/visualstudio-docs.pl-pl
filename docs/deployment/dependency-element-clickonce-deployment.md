---
title: "&lt;zależności&gt; elementu (wdrażania ClickOnce) | Dokumentacja firmy Microsoft"
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
helpviewer_keywords: <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: "27"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 8716da20c989a1a8d1e36d9e071e9802a06219bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;zależności&gt; elementu (wdrażania ClickOnce)
Identyfikuje wersji aplikacji do zainstalowania i lokalizacja manifestu aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `dependency` Element jest wymagany. Go nie ma żadnych atrybutów. Manifest rozmieszczenia może mieć wielu `dependency` elementów.  
  
 `dependency` Element najczęściej wyraża zależności dla aplikacji głównej zestawów zawartych w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Jeśli aplikacja Main.exe zużywa zestawu o nazwie DotNetAssembly.dll, ten zestaw musi być wymienione w sekcji zależności. Zależności, jednak może również express innych typów zależności, takich jak zależności na określoną wersję środowiska CLR, zestawu w globalnej pamięci podręcznej zestawów (GAC) lub obiektów COM. Ponieważ jest to technologia rozmieszczania bezobsługowego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nie może zainicjować pobranie i zainstalowanie tych typów zależności, ale uniemożliwia uruchomienie aplikacji co najmniej jeden określony zależności nie istnieją.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Wymagany. Ten element zawiera `assemblyIdentity` elementu. W poniższej tabeli przedstawiono atrybuty `dependentAssembly` obsługuje.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`preRequisite`|Opcjonalny. Określa, że ten zestaw powinna już istnieć w pamięci GAC. Prawidłowe wartości to `true` i `false`. Jeśli `true`oraz określonego zestawu nie istnieje w pamięci GAC, aplikacji nie powiedzie się.|  
|`visible`|Opcjonalny. Określa tożsamość aplikacji najwyższego poziomu, wraz z jego zależnościami. Używana wewnętrznie przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] do zarządzania przechowywania danych aplikacji i aktywacji.|  
|`dependencyType`|Wymagany. Relacja między tym zależności i aplikacji. Prawidłowe wartości to:<br /><br /> -   `install`. Składnik reprezentuje osobnej instalacji z bieżącej aplikacji.<br />-   `preRequisite`. Składnik jest wymagany przez bieżącą aplikację.|  
|`codebase`|Opcjonalny. Pełna ścieżka do manifestu aplikacji.|  
|`size`|Opcjonalny. Rozmiar manifest aplikacji w bajtach.|  
  
## <a name="assemblyidentity"></a>element assemblyIdentity  
 Wymagany. Ten element jest elementem podrzędnym `dependentAssembly` elementu. Zawartość `assemblyIdentity` musi być taka sama, jak opisano w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji. W poniższej tabeli przedstawiono atrybuty `assemblyIdentity` elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Określa nazwę aplikacji.|  
|`Version`|Wymagany. Określa numer wersji aplikacji, w następującym formacie:`major.minor.build.revision`|  
|`publicKeyToken`|Wymagany. Określa 16-znakowym ciągiem szesnastkowym reprezentujący ostatnich 8 bajtów skrótu SHA-1 klucza publicznego, pod którą jest podpisany aplikacji lub zestawu. Klucz publiczny używany do podpisywania musi wynosić 2048 bitów lub większej.|  
|`processorArchitecture`|Wymagany. Określa procesor. Prawidłowe wartości to `x86` dla 32-bitowego systemu Windows i `IA64` dla 64-bitowego systemu Windows.|  
|`Language`|Opcjonalny. Identyfikuje kodów języków dwie części zestawu. Na przykład EN-US, który oznacza dla języka angielskiego (US). Wartość domyślna to `neutral`. Tego elementu jest `asmv2` przestrzeni nazw.|  
|`type`|Opcjonalny. Dla zapewnienia zgodności z systemem Windows side-by-side zainstalować technologii. Jest to jedyna wartość dozwolonych `win32`.|  
  
## <a name="hash"></a>hash  
 `hash` Element jest opcjonalny element podrzędny `file` elementu. `hash` Element nie ma żadnych atrybutów.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]używa algorytmicznego skrót wszystkich plików w aplikacji w celu sprawdzenia zabezpieczeń, aby upewnić się, że żadne pliki nie zostały zmieniły po wdrożeniu. Jeśli `hash` element nie jest dołączana, to sprawdzenie nie zostanie wykonane. W związku z tym pominięcie `hash` element nie jest zalecane.  
  
## <a name="dsigtransforms"></a>DSIG:TRANSFORMS  
 `dsig:Transforms` Element jest elementem podrzędnym wymagane `hash` elementu. `dsig:Transforms` Element nie ma żadnych atrybutów.  
  
## <a name="dsigtransform"></a>DSIG:Transform  
 `dsig:Transform` Element jest elementem podrzędnym wymagane `dsig:Transforms` elementu. W poniższej tabeli przedstawiono atrybuty `dsig:Transform` elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Algorithm`|Algorytm używany do obliczania skrótu dla tego pliku. Obecnie tylko wartość używana przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>DSIG:DigestMethod  
 `dsig:DigestMethod` Element jest elementem podrzędnym wymagane `hash` elementu. W poniższej tabeli przedstawiono atrybuty `dsig:DigestMethod` elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Algorithm`|Algorytm używany do obliczania skrótu dla tego pliku. Obecnie tylko wartość używana przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>DSIG:DigestValue  
 `dsig:DigestValue` Element jest elementem podrzędnym wymagane `hash` elementu. `dsig:DigestValue` Element nie ma żadnych atrybutów. Wartość tekstu jest obliczona wartość skrótu dla określonego pliku.  
  
## <a name="remarks"></a>Uwagi  
 Manifesty wdrożenia zwykle mają jeden `assemblyIdentity` element, który identyfikuje nazwa i wersja manifestu aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład `dependency` element [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrażania.  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu określa zależność w zestawie zainstalowanym w pamięci GAC.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu określa zależności na określoną wersję środowiska CLR.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu określa zależność systemu operacyjnego.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<zależności > — Element](../deployment/dependency-element-clickonce-application.md)