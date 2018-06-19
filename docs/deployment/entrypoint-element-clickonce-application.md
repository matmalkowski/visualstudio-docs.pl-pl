---
title: '&lt;punkt wejścia&gt; elementu (aplikacji ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: beb140a64a415ab1a42f8157e2fafb1d20f9569a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31565253"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;punkt wejścia&gt; elementu (aplikacji ClickOnce)
Określa zestaw, który ma być wykonywane, kiedy to [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja jest uruchamiana na komputerze klienckim.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `entryPoint` Element jest wymagany i znajduje się w `urn:schemas-microsoft-com:asm.v2` przestrzeni nazw. Może istnieć tylko jedna `entryPoint` zdefiniowany w manifeście aplikacji element.  
  
 `entryPoint` Element ma następującego atrybutu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Opcjonalna. Ta wartość nie jest używana przez program .NET Framework.|  
  
 `entryPoint` zawiera następujące elementy.  
  
## <a name="assemblyidentity"></a>element assemblyIdentity  
 Wymagana. Rola `assemblyIdentity` i jego atrybuty jest zdefiniowany w [ \<assemblyIdentity > elementu](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 `processorArchitecture` Atrybutu tego elementu i `processorArchitecture` zdefiniowanych w atrybucie `assemblyIdentity` w innym miejscu w aplikacji manifestu musi być zgodna.  
  
## <a name="commandline"></a>Wiersz polecenia  
 Wymagana. Musi być elementem podrzędnym elementu `entryPoint` elementu. Nie ma elementów podrzędnych, a ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`file`|Wymagana. Lokalnego odwołania do zestawu uruchamiania dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Ta wartość nie może zawierać ukośnika (/) ani ukośnika odwrotnego (\\) separatorów ścieżek.|  
|`parameters`|Wymagana. Opisuje akcję wykonywaną z punktem wejścia. Jest jedyną poprawną wartością `run`; Jeśli zostanie podany ciąg pusty, `run` zakłada, że.|  
  
## <a name="customhostrequired"></a>customHostRequired  
 Opcjonalna. Jeśli jest włączone, określa, czy to wdrożenie zawiera składnik, który będzie wdrażany w ramach hosta niestandardowego, a nie jest aplikacją samodzielną.  
  
 Jeśli ten element jest obecny, `assemblyIdentity` i `commandLine` elementy nie mogą również być obecne. Jeśli są one [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zgłosi błąd sprawdzania poprawności podczas instalacji.  
  
 Ten element ma żadnych atrybutów i elementów podrzędnych.  
  
## <a name="customux"></a>customUX  
 Opcjonalna. Określa, że aplikacja jest zainstalowany i obsługiwanego przez instalatora niestandardowego i nie utworzenia wpisu menu Start, skrótu lub Dodaj lub usuń wpis programy.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Aplikacja, która zawiera customUX element musisz podać niestandardowego Instalatora, które używa <xref:System.Deployment.Application.InPlaceHostingManager> klasy do wykonania instalacji operacji. Nie można zainstalować aplikacji z tym elementem przez dwukrotne kliknięcie jej manifestu lub setup.exe wymagań wstępnych programu inicjującego. Niestandardowy Instalator można tworzyć elementy menu Start, skróty i wpisy Dodaj lub usuń programy. Jeśli niestandardowego Instalatora nie powoduje utworzenia wpisu Dodaj lub usuń programy, należy zapisać podany identyfikator subskrypcji przez <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> właściwości i umożliwiają użytkownikowi odinstalowanie aplikacji później przez wywołanie metody <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> metody. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie niestandardowego Instalatora dla aplikacji ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Uwagi  
 Ten element określa zestaw i punktu wejścia dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
 Nie można użyć `commandLine` do przekazania parametrów do aplikacji w czasie wykonywania. Można uzyskać dostępu do parametrów ciągu zapytania dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia z aplikacji <xref:System.AppDomain>. Aby uzyskać więcej informacji, zobacz [porady: pobieranie informacji o ciągu kwerendy w aplikacji ClickOnce w trybie Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `entryPoint` elementu w manifeście aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Ten przykładowy kod jest częścią większego przykładu udostępnionego dla [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md) tematu.  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)